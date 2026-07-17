# 🏋️‍♂️ Ejercicios: Comandos Avanzados y Flujos

Registro de comandos utilizados para resolver el laboratorio del Bloque 4 basándonos en la práctica real con la transcripción del curso en formato PDF.

## 📋 Enunciados del Bloque 4

1. **Muestra las primeras y las últimas líneas de un archivo de texto.**
2. **Busca una palabra específica en un archivo usando `grep`.**
3. **Cuenta el número de líneas de un archivo.**
4. **Redirecciona la salida de un comando para crear un archivo nuevo.**
5. **Añade información al final de un archivo existente utilizando redirecciones.**
6. **Combina dos comandos usando un pipe (`|`) (por ejemplo, filtra un listado).**
7. **Muestra todas las variables de entorno de tu sistema.**
8. **Muestra el valor de una variable de entorno específica.**
9. **Crea una variable de entorno temporal y comprueba que se haya guardado.**

---

## 🛠️ Resolución de la práctica

```bash
# Conversión previa del PDF de la clase a texto plano
pdftotext texto.pdf

# 1. Muestra las primeras y las últimas líneas de un archivo de texto
head texto.txt
tail texto.txt

# 2. Busca una palabra específica en un archivo usando grep
grep "21 - Variables de entorno" texto.txt

# 3. Cuenta el número de líneas de un archivo
wc -l texto.txt

# 4. Redirecciona la salida de un comando para crear un archivo nuevo
# (En el laboratorio se usó para volcar el PDF convertido)

# 5. Añade información al final de un archivo existente utilizando redirecciones (>>)
echo "Soy Mariano" >> texto.txt
tail texto.txt

# 6. Combina dos comandos usando un pipe (|) filtrando y contando líneas de forma correcta
grep "Soy" texto.txt | wc -l

# 7. Muestra todas las variables de entorno de tu sistema
env

# 8. Muestra el valor de una variable de entorno específica
echo $PUBLIC

# 9. Crea una variable de entorno temporal y comprueba que se haya guardado
MI_VARIABLE="Mariano"
echo $MI_VARIABLE