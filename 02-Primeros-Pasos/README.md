# 🐚 Bloque 2: Primeros Pasos en la Consola

En este bloque aprendemos los fundamentos para interactuar con la terminal, comprender dónde estamos parados, la diferencia entre rutas, comandos esenciales del sistema y cómo consultar la documentación integrada.

---

## 💻 5 - Hola Mundo

El clásico punto de partida. En Bash, utilizamos el comando `echo` para imprimir texto por pantalla.

- **Sintaxis:** `echo "texto"`
- **Ejemplos:**
  1. *Hola Mundo simple:* `echo "Hola Mundo desde Bash"`
  2. *Saber qué Shell estás usando:* `echo $SHELL` o `echo $0`

---

## 🔍 6 - Comandos de orientación

Sirven para saber exactamente en qué parte de la estructura de directorios nos encontramos y ver qué hay a nuestro alrededor.

### pwd (Print Working Directory)
Imprime la ruta de la carpeta actual en la que estás parado.
- **Sintaxis:** `pwd`

### ls (List)
Lista los archivos y carpetas del directorio actual.
- **Sintaxis:** `ls [opciones]`
- **Modificadores comunes:**
  - `ls -l` : Formato largo (detalla permisos, dueño, tamaño y fecha).
  - `ls -a` : Muestra todos los archivos, incluyendo los ocultos.
  - `ls -lh` : Formato largo pero con tamaños legibles por humanos.

---

## 🚀 7 - Comandos de navegación

Nos permiten movernos físicamente entre las distintas carpetas de nuestro sistema con `cd` (Change Directory).

- **Sintaxis:** `cd [ruta_destino]`
- **Ejemplos:**
  1. *Ir a una carpeta:* `cd curso`
  2. *Retroceder un nivel:* `cd ..`
  3. *Ir al directorio actual:* `cd .`
  4. *Ir a la carpeta personal (Home):* `cd ~` o simplemente `cd`

---

## 📍 8 - Ruta absoluta y relativa

Es vital entender la diferencia de cómo le indicamos al sistema a dónde queremos ir.

- **Ruta Relativa:** Se calcula desde la carpeta *donde estás parado actualmente*. No empieza con una barra diagonal `/`.
- **Ruta Absoluta:** Es la ruta completa *desde la raíz del disco duro*. Siempre comienza con una barra diagonal `/`.

---

## 🛠️ 9 - Otros comandos básicos

Comandos rápidos para obtener metadatos de nuestra sesión, máquina o sistema actual.

- `whoami` : Muestra el nombre del usuario con el que iniciaste sesión.
- `cal` : Muestra un calendario visual del mes actual.
- `date` : Muestra la fecha y la hora exacta del sistema.
- `uptime` : Indica cuánto tiempo lleva encendida la máquina.
- `hostname` : Muestra el nombre de red de tu computadora.
- `uname -a` : Muestra información completa del sistema operativo/Kernel.

---

## 🧬 10 - Anatomia del comando

Casi todos los comandos en sistemas Unix y Bash siguen una estructura estándar de tres componentes:

$$\text{Comando} + \text{Opción/es} + \text{Argumento/s}$$

- **Comando:** El programa principal que queremos ejecutar (ej: `ls`).
- **Opciones (Flags):** Modificadores que alteran el comportamiento (ej: `-la`).
- **Argumentos:** Los elementos sobre los cuales va a actuar el comando (ej: `/root/documento.txt`).

---

## 📚 11 - Ayuda y documentacion

No hace falta memorizarlo todo. Bash ofrece herramientas nativas para saber cómo usar cualquier comando.

### man (Manuales)
Abre la documentación exhaustiva del comando en el sistema.
- **Sintaxis:** `man [comando]` (ej: `man ls`).

### help / --help / -h
Muestra una ayuda rápida con la sintaxis de las herramientas en la terminal.

### Atajo para limpiar la consola
- `clear` : Limpia visualmente tu terminal (también podés usar `Ctrl + L`).