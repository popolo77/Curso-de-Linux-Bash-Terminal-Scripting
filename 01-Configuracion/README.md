# 🛠️ Bloque 1: Configuración Inicial

Este directorio está destinado a los apuntes teóricos, conceptos fundamentales y guías de instalación necesarios para preparar nuestro entorno de trabajo antes de empezar a escribir comandos y scripts.

---

## 📄 1 - Shell, Terminal y Bash

### Conceptos Clave
* **Terminal:** Es el programa de software (la interfaz gráfica) que nos permite interactuar con el sistema operativo a través de texto. Actúa como el contenedor o la "ventana".
* **Shell (Intérprete de comandos):** Es el programa interno que toma los comandos que escribimos en la terminal, los traduce y se los pasa al kernel del sistema operativo para que los ejecute.
* **Bash (Bourne Again Shell):** Es un tipo específico de Shell. Es el estándar y el más utilizado en la gran mayoría de las distribuciones Linux y en macOS (históricamente).

> **Nota:** La Terminal es la ventana donde escribís, la Shell es el cerebro que procesa lo que escribiste, y Bash es el "idioma/programa" específico que estamos usando.

---

## 📄 2 - Historia de Bash

* **Origen:** Creado por Brian Fox en 1989 para el proyecto GNU.
* **Evolución:** Nació como una mejora y reemplazo libre del Shell original de Unix: el *Bourne Shell* (`sh`). De ahí viene su juego de palabras en inglés: *Bourne Again Shell* (el Shell nacido de nuevo).
* **Importancia:** Se convirtió en el intérprete por defecto de casi todo el ecosistema Linux, transformándose en una herramienta fundamental para administradores de sistemas, desarrolladores y DevOps en todo el mundo.

---

## 📄 3 - Bash en Windows

Para quienes no utilizan Linux de forma nativa, existen excelentes alternativas para recrear el entorno Unix en Windows:

1.  **WSL (Windows Subsystem for Linux):** La opción recomendada. Permite correr una distribución real de Linux (como Ubuntu) de forma nativa dentro de Windows, compartiendo archivos de manera fluida.
2.  **Git Bash:** Una herramienta más ligera que viene incluida al instalar Git para Windows. Te ofrece una emulación muy fiel de la terminal Bash sin necesidad de virtualizar un sistema operativo completo.

---

## 📄 4 - Warp Terminal

**Warp** es un emulador de terminal moderno e inteligente basado en Rust. Cuenta con características que potencian la productividad:
* **Sugerencias con IA:** Ayuda a autocompletar comandos complejos y corregir errores en tiempo real.
* **Bloques de comandos:** Trata cada comando y su salida como un bloque independiente, permitiendo copiar el output o compartirlo de manera aislada muy fácilmente.
* **Navegación fluida:** Interfaz gráfica intuitiva con atajos similares a los de un editor de código moderno (como VS Code).

---

## 🎯 Próximos Pasos
Una vez finalizado y entendido este bloque de configuración, el entorno estará listo para avanzar al **Bloque 2: Primeros Pasos en la Consola**, donde crearemos nuestro primer *"Hola Mundo"* y empezaremos a navegar por el sistema de archivos.