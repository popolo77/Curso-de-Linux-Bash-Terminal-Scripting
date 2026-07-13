# 🐚 Bloque 2: Primeros Pasos en la Consola

En este bloque aprendemos los fundamentos para interactuar con la terminal, comprender dónde estamos parados, la diferencia entre rutas, comandos esenciales del sistema y cómo consultar la documentación integrada.

---

## 💻 5 - Hola Mundo

El clásico punto de partida. En Bash, utilizamos el comando `echo` para imprimir texto por pantalla.

* **Sintaxis:**
    ```bash
    echo "texto"
    ```
* **Ejemplos:**
    1.  **Hola Mundo simple:**
        ```bash
        echo "Hola Mundo desde Bash"
        ```
    2.  **Saber qué Shell estás usando (Variables del sistema):**
        ```bash
        echo $SHELL
        # o también:
        echo $0
        ```
        *Esto imprimirá `/bin/bash` si estás configurado correctamente.*

---

## 🔍 6 - Comandos de Orientación

Sirven para saber exactamente en qué parte de la estructura de directorios nos encontramos y ver qué hay a nuestro alrededor.

### `pwd` (Print Working Directory)
Imprime la ruta de la carpeta actual en la que estás parado.
* **Sintaxis:**
    ```bash
    pwd
    ```
* **Ejemplo:**
    ```bash
    localhost:~# pwd
    /root
    ```

### `ls` (List)
Lista los archivos y carpetas del directorio actual.
* **Sintaxis:**
    ```bash
    ls [opciones]
    ```
* **Modificadores comunes:**
    * `ls -l`: Formato largo (detalla permisos, dueño, tamaño y fecha).
    * `ls -a`: Muestra todos los archivos, incluyendo los ocultos (aquellos que empiezan con un punto `.`).
    * `ls -lh`: Formato largo pero con tamaños legibles por humanos (ej: `5.0K` en vez de `5105` bytes).
    * *Se pueden combinar:* `ls -la` o `ls -lah`.

---

## 🚀 7 - Comandos de Navegación

Nos permiten movernos físicamente entre las distintas carpetas de nuestro sistema con `cd` (Change Directory).

* **Sintaxis:**
    ```bash
    cd [ruta_destino]
    ```
* **Ejemplos:**
    1.  **Ir a una carpeta:** `cd curso`
    2.  **Retroceder un nivel (ir a la carpeta padre):** `cd ..`
    3.  **Ir al directorio actual (útil para ejecuciones):** `cd .`
    4.  **Ir a la carpeta personal (Home):** `cd ~` o simplemente `cd`
    5.  **Navegación interactiva:** Escribir `cd ` y presionar la tecla **Tabulador** para autocompletar o ver sugerencias de carpetas disponibles.
    6.  **Navegación concatenada:** Podés encadenar rutas para moverte varios niveles de un solo golpe:
        ```bash
        cd .git/logs/refs/remotes
        ```

---

## 📍 8 - Ruta Absoluta y Relativa

Es vital entender la diferencia de cómo le indicamos al sistema a dónde queremos ir.

* **Ruta Relativa:** Se calcula desde la carpeta **donde estás parado actualmente**. No empieza con una barra diagonal `/`.
    * *Ejemplo:* Si estás en `/root` y querés ir a `/root/curso`, simplemente escribís: `cd curso`.
* **Ruta Absoluta:** Es la ruta completa **desde la raíz del disco duro**. Siempre comienza con una barra diagonal `/` (que representa la raíz del sistema).
    * *Ejemplo:* No importa dónde estés parado, si escribís: `cd /root/curso`, te llevará directamente allí.

---

## 🛠️ 9 - Otros Comandos Básicos (Información del Sistema)

Comandos rápidos para obtener metadatos de nuestra sesión, máquina o sistema actual.

* **`whoami`**: Muestra el nombre del usuario con el que iniciaste sesión.
    ```bash
    whoami
    # Devuelve: root
    ```
* **`cal`**: Muestra un calendario visual del mes actual.
    ```bash
    cal
    ```
* **`date`**: Muestra la fecha y la hora exacta del sistema.
    ```bash
    date
    ```
* **`uptime`**: Indica cuánto tiempo lleva encendida la máquina y la carga del sistema.
    ```bash
    uptime
    ```
* **`hostname`**: Muestra el nombre de red que tiene asignado tu computadora.
    ```bash
    hostname
    ```
* **`uname`**: Muestra información del sistema operativo/Kernel.
    * `uname -a` nos da el reporte completo de la arquitectura del procesador, versión de kernel, etc.

---

## 🧬 10 - Anatomía del Comando

Casi todos los comandos en sistemas Unix y Bash siguen una estructura estándar de tres componentes:

$$\text{Comando} + \text{Opción/es} + \text{Argumento/s}$$

* **Comando:** El programa principal que queremos ejecutar (ej: `ls`).
* **Opciones (Flags):** Modificadores que alteran el comportamiento del comando. Se anteponen con uno o dos guiones (ej: `-la` o `--help`).
* **Argumentos:** Los elementos sobre los cuales va a actuar el comando, como rutas de archivos o textos (ej: `/root/documento.txt`).

*Ejemplo:* En `ls -l /var/log`, `ls` es el comando, `-l` es la opción y `/var/log` es el argumento.

---

## 📚 11 - Ayuda y Documentación

No hace falta memorizarlo todo. Bash ofrece herramientas nativas para saber cómo usar cualquier comando.

### `man` (Manuales)
Abre la documentación exhaustiva del comando en el sistema.
* **Sintaxis:** `man [comando]` (ej: `man ls`).
* *Para navegar:* Usá las flechas del teclado y presioná la tecla **`q`** para salir del manual.

### `help` / `--help` / `-h`
Muestra una ayuda rápida con la sintaxis de las herramientas en la terminal.
* **Sintaxis:** `[comando] --help` o `[comando] -h` (ej: `python3 --help`).
* *Nota:* Para comandos puros de la Shell, podés usar el comando interno `help cd`.

### Atajo para limpiar la consola
* `clear`: Limpia visualmente tu terminal para arrancar limpio de nuevo (también podés usar el atajo **`Ctrl + L`**).