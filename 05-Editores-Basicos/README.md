Markdown
# 📝 Bloque 5: Editores de Texto en Terminal

En este bloque aprendemos a crear y modificar archivos directamente desde la línea de comandos sin depender de una interfaz gráfica, una habilidad clave para administrar servidores o editar archivos de forma rápida.

---

## 📖 23 - Introducción a editores básicos

Cuando trabajamos en una terminal pura, necesitamos herramientas que corran dentro de la misma consola. Se dividen principalmente en editores secuenciales (fáciles de usar, con atajos visibles) y editores modales (potentes, basados en diferentes modos de teclado).

---

## 📖 24 - Nano

Es el editor más amigable e intuitivo para arrancar en el mundo de la terminal.
* **Abrir/Crear:** `nano archivo.txt`
* **Navegación:** Únicamente con las flechas del teclado.
* **Atajos clave:**
  * `Ctrl + O` : Guardar el archivo (escribir cambios).
  * `Ctrl + X` : Salir del editor.
  * `Ctrl + W` : Buscar texto dentro del archivo.

---

## 📖 25 - Vim (Vi Improved)

Es un editor avanzado y **modal**, lo que significa que las teclas hacen cosas distintas según el modo en el que te encuentres.
* **Abrir/Crear:** `vim archivo.txt`
* **Modos principales:**
  1. *Modo Comando (Por defecto):* Sirve para moverse, borrar o copiar texto. No permite escribir de forma directa.
  2. *Modo Inserto:* Permite escribir texto real. Se ingresa presionando la tecla `i` y se sale con `Esc`.
  3. *Modo Línea de Comandos:* Para órdenes del sistema (guardar, salir). Se ingresa escribiendo `:` desde el Modo Comando.
* **Cómo salir de Vim:**
  * `:q`  -> Salir (si no hay cambios sin guardar).
  * `:wq` -> Guardar cambios y salir (**w**rite and **q**uit).
  * `:q!` -> Forzar la salida descartando todos los cambios.

---

## 📖 26 - Otros editores (Neovim / Emacs)

* **Neovim (`nvim`):** Una evolución moderna de Vim, ultra extensible, rápida y muy elegida por desarrolladores en la actualidad.
* **Emacs:** Un entorno de edición masivo y configurable, pero con una curva de aprendizaje alta debido a sus complejas combinaciones de teclas.
2️⃣ El archivo de Ejercicios Resueltos (Simulando tu entorno Git Bash)
Ruta: 05-Editores-Basicos/ejercicios/README.md