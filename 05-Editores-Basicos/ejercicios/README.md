Markdown
# 🏋️‍♂️ Ejercicios: Editores de Texto en Terminal

Registro de comandos y pasos utilizados para resolver el laboratorio del Bloque 5 interactuando con los editores nativos.

## 📋 Enunciados del Bloque 5

1. **Crea un archivo nuevo utilizando el editor `nano`.**
2. **Escribe varias líneas de texto dentro del archivo en `nano`, guárdalo y sal del editor.**
3. **Abre el archivo que acabas de crear utilizando ahora el editor `vim`.**
4. **Entra en el modo inserción de `vim` e introduce una nueva línea de texto.**
5. **Sal del modo inserción de `vim`, guarda los cambios y sal del editor.**
6. **Vuelve a abrir el archivo con `vim`, realiza modificaciones y sal sin guardar los cambios (forzar la salida).**
7. **Comprueba desde la terminal (usando comandos del Bloque 4) que los cambios guardados se aplicaron correctamente y los no guardados se descartaron.**

---

## 🛠️ Resolución de la práctica

### Pasos ejecutados en la consola:

1. **Creación del archivo con Nano:**
   ```bash
   nano practica_editores.txt
Edición en Nano:
Se escribieron dos líneas de texto de prueba, se guardó con Ctrl + O, se confirmó con Enter y se cerró con Ctrl + X.

Apertura en Vim:

Bash
vim practica_editores.txt
Inserción de texto en Vim:
Se presionó la tecla i para entrar en -- INSERT -- y se redactó una tercera línea de texto.

Guardado en Vim:
Se presionó Esc para volver al modo comando y se ejecutó el comando de cierre:

Bash
:wq
Modificación fallida (Forzar salida):
Se reabrió el archivo con vim practica_editores.txt, se borró una línea en modo inserto, se presionó Esc y se descartó el cambio forzando la salida con:

Bash
:q!
Comprobación final del archivo:

Bash
cat practica_editores.txt
Resultado: El comando mostró las líneas guardadas originalmente en Nano y la agregada en el paso 5 de Vim. La modificación del paso 6 no se aplicó, confirmando el correcto funcionamiento de los editores.