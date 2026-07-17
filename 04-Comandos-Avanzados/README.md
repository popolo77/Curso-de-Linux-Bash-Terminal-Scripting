# 🔧 Bloque 4: Comandos Avanzados y Flujos

En este bloque aprendemos a inspeccionar el contenido de los archivos, realizar filtros de texto avanzados, encadenar comandos mediante tuberías y gestionar variables de entorno del sistema.

---

## 📖 18 - Lectura de archivos

Dependiendo del tamaño del archivo y de lo que necesitemos hacer, Bash nos ofrece distintas herramientas para visualizar contenido:

- `cat` **(Concatenate):** Muestra todo el contenido del archivo de golpe en la pantalla. Ideal para archivos cortos.
- `less` **:** Abre un visor interactivo para navegar página por página. Usa `q` para salir. Ideal para archivos gigantes.
- `head` **:** Muestra las primeras 10 líneas de un archivo (o las que indiques con `-n`).
- `tail` **:** Muestra las últimas 10 líneas de un archivo. Su opción `tail -f` permite ver cambios en tiempo real (monitoreo de logs).

---

## 🔍 19 - Búsqueda y recuento

- `grep` **:** Busca un patrón de texto dentro de los archivos. Es ultra potente.
  - `grep -i "texto" archivo.txt` : Ignora mayúsculas/minúsculas.
  - `grep -r "texto" .` : Busca recursivamente en toda la carpeta actual.
- `wc` **(Word Count):** Cuenta elementos. El modificador más usado es `wc -l`, que cuenta las líneas de un archivo o entrada.

---

## 🔀 20 - Redirecciones y Pipes (Tuberías)

Modifican la entrada y salida estándar de los comandos:

- `>` **(Redirección simple):** Guarda la salida de un comando en un archivo, sobrescribiendo su contenido previo.
- `>>` **(Redirección de adjunto):** Agrega la salida al final del archivo sin borrar lo anterior.
- `|` **(Pipe / Tubería):** Conecta comandos. Pasa la salida del primer comando como entrada directa del segundo.

---

## 🌐 21 - Variables de entorno

Espacios de memoria que almacenan configuraciones del sistema:

- `printenv` o `env` : Lista todas las variables de entorno activas.
- `echo $VARIABLE` : Muestra el valor de una variable específica (ej: `$USER`, `$PATH`, `$SHELL`).
- `MI_VAR="valor"` : Define una variable local y temporal para la sesión actual.