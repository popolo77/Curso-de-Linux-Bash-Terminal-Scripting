# 🛡️ Bloque 6: Administración del Sistema y Permisos

En este bloque aprendemos en profundidad cómo Linux gestiona la seguridad, quién puede acceder, modificar o ejecutar archivos y carpetas, cómo funcionan los permisos en formato octal y simbólico, la matemática de la máscara de permisos (`umask`) y la administración con el superusuario (`sudo`).

---

## 📖 28 - Tipos de Permisos y Usuarios

En Linux, la seguridad es la piedra angular. Cada elemento del sistema pertenece a un usuario y a un grupo, y define reglas estrictas para tres niveles de usuarios.

### 👤 Los 3 Niveles de Usuarios:
* **`u` (User / Owner - Propietario):** El usuario creador del archivo o carpeta.
* **`g` (Group - Grupo):** Conjunto de usuarios que comparten los mismos privilegios sobre el archivo.
* **`o` (Others - Otros):** Cualquier otra persona con acceso al sistema (el resto del mundo).

### 🔑 Los 3 Tipos de Permisos Básicos:
* **`r` (Read / Lectura):** 
  * *En Archivos:* Permite abrir y ver su contenido (`cat`, `less`).
  * *En Directorios:* Permite listar los archivos que contiene (`ls`).
* **`w` (Write / Escritura):** 
  * *En Archivos:* Permite modificar su texto o borrar el archivo.
  * *En Directorios:* Permite crear, renombrar o eliminar archivos dentro de él.
* **`x` (Execute / Ejecución):** 
  * *En Archivos:* Permite correr el archivo como un script o programa ejecutable.
  * *En Directorios:* Permite entrar dentro de la carpeta con el comando `cd`.

---

## 📖 29 - Anatomía de los Permisos (`ls -l`)

Cuando ejecutamos `ls -l` en la terminal, la primera columna nos muestra 10 caracteres que definen la estructura completa de acceso:

```text
- r w x r - x r - -
| |---| |---| |---|
|   |     |     └─> Permisos de Otros (o): r-- (solo lectura)
|   |     └───────> Permisos del Grupo (g): r-x (lectura y ejecución)
|   └─────────────> Permisos del Propietario (u): rwx (control total)
└─────────────────> Tipo de elemento: (-) archivo plano | (d) directorio


---

## 📖 30 - Modificación de Permisos (`chmod` / `chown`)

Existen dos formas principales de cambiar los permisos de un archivo o carpeta mediante el comando `chmod`:

### 1. MODO SIMBÓLICO (Usando letras)

Sintaxis: `chmod [usuario][operador][permiso] archivo`

* **Usuarios:** `u` (owner), `g` (group), `o` (others), `a` (all / todos).
* **Operadores:** `+` (agregar), `-` (quitar), `=` (asignar exactamente).
* **Ejemplo 1:** Dar permiso de ejecución solo al propietario sobre un script:
```bash
chmod u+x script.sh

```


* **Ejemplo 2:** Quitarle permiso de lectura y escritura al grupo y a otros:
```bash
chmod go-rw documento.txt

```



---

### 2. MODO OCTAL (Usando números y suma binaria)

A cada letra de permiso se le asigna un valor numérico fijo:

* **`r` (Lectura) = 4**
* **`w` (Escritura) = 2**
* **`x` (Ejecución) = 1**
* **Sin permiso (`-`) = 0**

Sumando estos valores obtenemos un dígito del 0 al 7 para cada nivel (Owner, Group, Others):

| Suma | Permisos | Significado |
| --- | --- | --- |
| **7** (4+2+1) | `rwx` | Control total (Lectura, escritura y ejecución) |
| **6** (4+2+0) | `rw-` | Lectura y escritura (Estándar para archivos planos) |
| **5** (4+0+1) | `r-x` | Lectura y ejecución (Estándar para carpetas/scripts) |
| **4** (4+0+0) | `r--` | Solo lectura |
| **0** (0+0+0) | `---` | Ningún permiso (Bloqueado) |

#### 💡 Ejemplo práctico de lectura de un código octal (`chmod 755`):

* **Primer número (7):** $4+2+1 = \text{Propietario tiene } rwx$
* **Segundo número (5):** $4+0+1 = \text{Grupo tiene } r-x$
* **Tercer número (5):** $4+0+1 = \text{Otros tienen } r-x$

```bash
# Asigna rwxr-xr-x (Control total al usuario, lectura y ejecución a los demás)
chmod 755 mi_script.sh

```

---

### Cambiar de propietario (`chown`)

Para transferir la propiedad de un archivo a otro usuario del sistema se utiliza `chown`:

```bash
sudo chown usuario_nuevo archivo.txt

```

---

## 📖 31 - Máscara de Permisos (`umask`)

### ¿Por qué existe `umask`?

Cuando creás un archivo con `touch` o una carpeta con `mkdir`, el sistema operativo debe decidir qué permisos asignarles automáticamente. `umask` es el "filtro" que resta permisos al máximo teórico por defecto.

### Los Máximos Teóricos de Linux:

* **Para Carpetas:** Máximo **`777`** (`rwxrwxrwx`) -> Necesitan ejecución (`x`) para poder entrar con `cd`.
* **Para Archivos:** Máximo **`666`** (`rw-rw-rw-`) -> Nunca nacen ejecutables por motivos de seguridad.

### La Matemática del Filtro:

Si consultamos la máscara actual en la consola:

```bash
$ umask
0022

```

*(Nos enfocamos en los tres últimos dígitos: `022`)*.

El valor `022` se **resta** del máximo teórico al crear un elemento:

1. **Al crear una CARPETA:**

$$777 \text{ (Máximo)} - 022 \text{ (Máscara)} = 755 \text{ (Permiso resultante: } drwxr-xr-x)$$


2. **Al crear un ARCHIVO:**

$$666 \text{ (Máximo)} - 022 \text{ (Máscara)} = 644 \text{ (Permiso resultante: } -rw-r--r--)$$



#### 🧪 Ejemplo práctico cambiando la máscara:

Si queremos que todo lo que creemos nazca siendo **privado** (accesible solo para nuestro usuario):

```bash
# Cambiamos la máscara para restar todo privilegio a grupo y otros (077)
umask 0077

# Creamos un archivo
touch mi_secreto.txt

# Verificamos sus permisos (666 - 077 = 600)
ls -l mi_secreto.txt
# Resultado: -rw------- (Solo el usuario lee y escribe)

```

---

## 📖 32 - Superusuario (`sudo` / `su`)

En Linux, el usuario **Root** es el administrador supremo con poder ilimitado para modificar cualquier archivo del sistema.

* **`sudo` (SuperUser DO):** Permite a un usuario normal ejecutar un comando puntual con privilegios de Root.
* **Ejemplo:** `sudo apt update`


* **`su` (Switch User):** Permite cambiar temporalmente a la sesión de otro usuario o a Root directamente.

> ⚠️ **Advertencia Didáctica:** Usar `sudo` implica saltarse todas las protecciones de permisos de Linux. Un comando destructivo como `sudo rm -rf /` borraría la totalidad del disco sin pedir confirmación.

```

---

Una vez que guardes este archivo con `Ctrl + S`, podemos subir todo a GitHub con un commit bien claro:

```bash
git add 06-Administracion-Permisos/README.md
git commit -m "docs: reestructura el README del bloque 6 con ejemplos didacticos"
git push origin main

```

¿Qué tal se siente este formato para encarar el **Bloque 7**?