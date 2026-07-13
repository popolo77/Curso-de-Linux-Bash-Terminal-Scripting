¡Qué gran sesión de práctica en Git Bash (MINGW64) de Windows! Pasaste por casi todo el temario del bloque. Se nota que estuviste navegando, listando en detalle, buscando manuales, rebotando contra comandos no encontrados (como `man` y `cal` que no vienen por defecto en Git Bash, ¡un clásico!) y probando la ayuda de `ls` y `cd`.

Acá tenés el **README de tu práctica** estructurado, limpio y detallado con la explicación de cada paso que diste en tu terminal. Lo podés guardar como `README.md` dentro de tu carpeta `02-Primeros-Pasos/ejercicios/` (o donde guardes tus resoluciones).

---

# 📝 Resolución - Ejercicios: Primeros Pasos

Este archivo contiene el registro detallado y la explicación paso a paso de los comandos ejecutados en la terminal de Git Bash (`MINGW64`) para resolver los ejercicios prácticos del Bloque 2.

---

## 🛠️ Paso a Paso de la Práctica

### 1. Ubicación y Navegación Relativa

Primero, confirmamos dónde estábamos parados en el sistema y nos movimos a la carpeta de Documentos usando una **ruta relativa**:

```bash
$ pwd
/c/Users/grabador

$ cd Documents

```

* **Explicación:** `pwd` nos indicó que nos encontrábamos en nuestro directorio personal (`/c/Users/grabador`). Al escribir `cd Documents` (sin barra `/` inicial), el sistema buscó la carpeta "Documents" directamente dentro de nuestra ubicación actual.

---

### 2. Navegación con Ruta Absoluta

Una vez dentro de Documentos, probamos movernos utilizando **rutas absolutas** (indicando el camino completo desde la raíz `/`):

```bash
$ pwd
/c/Users/grabador/Documents

$ cd /c/Users/grabador

$ cd /c/Users/grabador/Documents

```

* **Explicación:** No importa en qué directorio estemos parados, al escribir una ruta que inicia con `/` (ej: `/c/Users/grabador`), la terminal nos traslada de forma directa a esa ubicación exacta en el disco.

---

### 3. Retroceder un Nivel

Volvimos a nuestra carpeta de usuario subiendo un escalón en la jerarquía de carpetas:

```bash
$ cd ..

$ pwd
/c/Users/grabador

```

* **Explicación:** El argumento especial `..` le indica a `cd` que queremos movernos a la carpeta "padre" de la actual (en este caso, salimos de `Documents` para volver a `grabador`).

---

### 4. Listado en Diferentes Formatos (Simple, Largo y Oculto)

Exploramos el contenido de nuestro directorio personal aplicando diferentes opciones al comando `ls`:

* **Listado Simple:**
```bash
$ ls
AppData/  Desktop/  Documents/  Downloads/  Pictures/  ...

```


* **Listado Detallado (Formato Largo):**
```bash
$ ls -l
total 6741
drwxr-xr-x 1 grabador 197121       0 Jun 11 08:01  Documents/
-rw-r--r-- 1 grabador 197121 4194304 Jul 11 13:24  NTUSER.DAT

```


*Muestra permisos, propietario, grupo, tamaño en bytes y fecha de modificación.*
* **Listado de Archivos Ocultos:**
```bash
$ ls -a
./  ../  .bash_history  .gitconfig  AppData/  ...

```


*Aquí logramos revelar archivos de configuración ocultos como `.bash_history` y `.gitconfig` que omitíamos en el listado común.*

---

### 5. Intentos con `man` (Manuales de Sistema)

Intentamos abrir los manuales de `cd` y `ls` usando `man`:

```bash
$ man cd
bash: man: command not found

```

* **¿Qué pasó acá?** El comando `man` es nativo de sistemas Linux/Unix reales. Al estar practicando en Windows mediante **Git Bash**, este entorno ligero no incluye por defecto la base de datos de manuales de ayuda. ¡Es totalmente normal que falle!

---

### 6. Consulta de Ayuda Alternativa (`--help` y `help`)

Dado que no teníamos `man`, recurrimos a los flags de ayuda incorporados para consultar la documentación de `ls` y el comando integrado `cd`:

```bash
$ ls --help
Usage: ls [OPTION]... [FILE]...
...

$ cd --help
cd: cd [-L|[-P [-e]]] [-@] [dir]
...

```

* **Explicación:** Usar `--help` invoca la ayuda rápida del comando. En el caso de `cd` (al ser un comando interno de la propia Shell Bash), también se puede consultar usando el comando `help cd`.

---

### 7. Información del Sistema

Consultamos metadatos de nuestra sesión y fecha actual:

```bash
$ date
Mon Jul 13 20:53:57     2026

$ whoami
grabador

```

* *Nota:* Al intentar usar `cal` para ver el calendario, nos devolvió `command not found` debido a que este programa tampoco viene preinstalado en la versión básica de Git Bash para Windows.

---

### 8. Regreso al Inicio y Limpieza

Para finalizar la sesión de práctica de forma ordenada, nos aseguramos de volver al directorio Home y limpiamos la pantalla de la consola:

```bash
$ cd

$ clear

```

* **Explicación:** Ejecutar `cd` sin argumentos nos devuelve automáticamente a nuestra Home (`~`). El comando `clear` (o el atajo `Ctrl + L`) limpia la pantalla para eliminar el ruido visual de los comandos anteriores.

---

¿Qué te parece cómo quedó registrado? Si ya querés ir avanzando con el **Bloque 3 (Gestión de Archivos y Directorios)** para aprender a crear, copiar y borrar cosas, metele play al video y pasame lo que vayas escribiendo en la terminal.