# 📁 Bloque 3: Gestión de Archivos y Directorios

En este bloque aprendemos a interactuar profundamente con el sistema. Ya no solo nos movemos y miramos, sino que ahora empezamos a manipular directorios, copiar, mover, renombrar y borrar archivos, además de hacer búsquedas avanzadas.

---

## 📂 13 - Sistema de archivos Unix

Aunque Bash se puede usar en Windows (vía WSL o Git Bash), su estructura nativa pertenece a los sistemas Unix/Linux. Conocer los directorios por defecto es fundamental:

- `/` **(Raíz):** El origen de todo el sistema de archivos.
- `/home` **(o `/Users`):** Carpeta personal de los usuarios.
- `/etc` **:** Archivos de configuración del sistema.
- `/bin` **:** Archivos binarios ejecutables (los comandos básicos del sistema).
- `/usr` **:** Software y utilidades adicionales instaladas para el usuario.
- `/var` **:** Archivos variables, como bases de datos o *logs* (registros) del sistema.
- `/tmp` **:** Archivos temporales (el sistema suele vaciar esta carpeta automáticamente).

---

## 🗂️ 14 - Manipulacion de archivos y directorios

Aquí están los comandos esenciales para la creación y destrucción de elementos en nuestra terminal.

### mkdir (Make Directory)
Crea una o varias carpetas nuevas.
- **Sintaxis:** `mkdir [nombre_carpeta]`
- **Ejemplo:** `mkdir curso_bash`

### cp (Copy)
Copia archivos o directorios de un lugar a otro.
- **Sintaxis:** `cp [origen] [destino]`
- **Ejemplo Archivo:** `cp licencia.txt copia_licencia.txt`
- **Copia Recursiva (Carpetas):** Para copiar una carpeta y todo su contenido adentro, es OBLIGATORIO usar la opción `-r` o `-a`.
  - `cp -r carpeta_origen/ carpeta_destino/`

### mv (Move / Rename)
Sirve para dos cosas: mover archivos a otra ruta, o renombrarlos si se mantienen en la misma ruta.
- **Mover:** `mv licencia.txt curso/` (Mueve el archivo adentro de la carpeta curso).
- **Renombrar:** `mv archivo.txt nuevo_nombre.txt` (Le cambia el nombre en el mismo lugar).

### rm (Remove)
Elimina archivos y directorios de forma permanente (¡Cuidado, no van a la papelera!).
- **Borrar archivo:** `rm archivo.txt`
- **Borrar carpeta (Recursivo):** `rm -r carpeta/` (Borra la carpeta y todo lo que tiene adentro).
- **Borrado Interactivo:** `rm -ri carpeta/` (Te pregunta confirmación antes de borrar cada cosa, ideal para no equivocarse).
- ⚠️ **Borrado Forzado:** `rm -rf carpeta/` (Borra todo sin preguntar. **Usar con muchísima precaución** para no romper el sistema).

---

## 🃏 15 - Wildcards (Comodines)

Los comodines nos permiten seleccionar múltiples archivos a la vez basándonos en patrones de texto.

### El asterisco (`*`)
Representa **cero o más** caracteres. Es un "todo lo que coincida".
- `ls *.txt` : Lista todos los archivos que terminen en `.txt`.
- `ls 03*` : Lista todo lo que empiece con `03`.
- `rm *.md` : Borra todos los archivos Markdown de la carpeta.

### El signo de interrogación (`?`)
Representa **un único carácter exacto**.
- `ls a?.txt` : Buscará archivos como `ab.txt` o `a1.txt`, pero NO `abc.txt`.
- `ls ????.*` : Buscará cualquier archivo que tenga exactamente 4 letras antes del punto.

---

## 🌳 16 - Listados avanzados

Cuando los proyectos crecen, `ls` puede quedarse corto.

### tree
Muestra el contenido de un directorio y sus subdirectorios en forma de árbol visual. *(Nota: En Git Bash o algunos sistemas puede requerir instalación previa).*
- **Sintaxis:** `tree`
- **Ejemplo:** `tree -a` (Muestra el árbol incluyendo archivos ocultos).

### find
Una herramienta extremadamente potente para buscar archivos dentro del sistema basándose en distintos criterios.
- **Sintaxis básica:** `find [ruta] [criterio] [patrón]`
- **Ejemplo de búsqueda por nombre:** `find . -name "README.md"` (Busca el archivo exacto en el directorio actual y sus subcarpetas).
- **Ejemplo combinado con Wildcards:** `find . -name "*.txt"` (Encuentra todos los archivos de texto desde donde estás parado hacia abajo).