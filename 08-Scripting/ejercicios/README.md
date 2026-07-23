# 🏋️‍♂️ Ejercicios Resueltos - Bloque 8: Introducción al Scripting

Este directorio contiene las soluciones prácticas para las lecciones de introducción al scripting en Bash, cubriendo conceptos clave como sintaxis básica, variables, lectura interactiva con `read`, parámetros posicionales y operaciones aritméticas.

---

## 📋 Lista de Ejercicios y Enunciados

### 1. Hola Mundo (`ejercicio1.sh`)
> **Consigna:** Crear un script que imprima por pantalla el mensaje: `"Hola, mundo desde Bash."`.
```bash
#!/bin/bash
echo "Hola, mundo desde Bash."

```

---

### 2. Sistema y Fecha (`ejercicio2.sh`)

> **Consigna:** Crear un script que muestre la fecha actual del sistema y el directorio de trabajo actual.

```bash
#!/bin/bash
echo "Fecha actual: $(date)"
echo "Directorio actual: $(pwd)"

```

---

### 3. Uso de Variables (`ejercicio3.sh`)

> **Consigna:** Crear un script que guarde tu nombre en una variable y lo muestre por pantalla.

```bash
#!/bin/bash
NOMBRE="Mariano"
echo "Hola, mi nombre es $NOMBRE."

```

---

### 4. Operaciones Aritméticas Básicas (`ejercicio4.sh`)

> **Consigna:** Crear un script que declare dos variables numéricas y muestre el resultado de sumarlas, restarlas y multiplicarlas.

```bash
#!/bin/bash
num1=10
num2=5

echo "Número 1: $num1 \vert{} Número 2: $num2"
echo "Suma: $((num1 + num2))"
echo "Resta: $((num1 - num2))"
echo "Multiplicación: $((num1 * num2))"

```

---

### 5. Lectura Interactiva (`ejercicio5.sh`)

> **Consigna:** Crear un script que pida al usuario su nombre mediante la instrucción `read` y lo salude.

```bash
#!/bin/bash
read -p "Por favor, ingresá tu nombre: " NOMBRE
echo "¡Bienvenido/a, $NOMBRE!"

```

---

### 6. Suma Interactiva (`ejercicio6.sh`)

> **Consigna:** Crear un script que pida dos números al usuario e imprima su suma por pantalla.

```bash
#!/bin/bash
read -p "Ingresá el primer número: " n1
read -p "Ingresá el segundo número: " n2

suma=$((n1 + n2))
echo "El resultado de la suma es: $suma"

```

---

### 7. Parámetros Posicionales (`ejercicio7.sh`)

> **Consigna:** Crear un script que reciba tres argumentos posicionales y muestre por pantalla únicamente el primero y el tercero.

```bash
#!/bin/bash
echo "Primer argumento (\$1): $1"
echo "Tercer argumento (\$3): $3"

```

---

### 8. Total de Argumentos Recibidos (`ejercicio8.sh`)

> **Consigna:** Crear un script que reciba una cantidad indeterminada de argumentos y muestre el número total de parámetros pasados.

```bash
#!/bin/bash
echo "Cantidad total de argumentos recibidos (\$#): $#"

```

---

### 9. Calculadora con Argumentos (`ejercicio9.sh`)

> **Consigna:** Crear un script que reciba dos números como argumentos de consola y muestre la suma, resta, multiplicación y división entre ellos.

```bash
#!/bin/bash
num1=$1
num2=$2

echo "--- Calculadora por Argumentos ---"
echo "Suma: $((num1 + num2))"
echo "Resta: $((num1 - num2))"
echo "Multiplicación: $((num1 * num2))"
echo "División: $((num1 / num2))"

```

---

### 10. Creación y Escritura de Archivo (`ejercicio10.sh`)

> **Consigna:** Crear un script que genere automáticamente un archivo de texto llamado `resultado.txt` y guarde tu nombre dentro de él.

```bash
#!/bin/bash
NOMBRE="Mariano"
ARCHIVO="resultado.txt"

echo "Hola, mi nombre es $NOMBRE" > $ARCHIVO
echo "Archivo '$ARCHIVO' creado exitosamente."

```

---

## 🛠️ Instrucciones de Ejecución

Para ejecutar cualquiera de estos scripts en la terminal, asegúrate de otorgarles primero permisos de ejecución mediante el comando `chmod`:

```bash
# 1. Otorgar permisos de ejecución
chmod +x ejercicio*.sh

# 2. Ejemplo de ejecución directa:
./ejercicio1.sh

# 3. Ejemplo de ejecución con argumentos (Ejercicios 7, 8 y 9):
./ejercicio9.sh 10 2

```
