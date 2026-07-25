# 🧠 Bloque 9: Lógica de Programación en Bash

En este bloque abordamos las estructuras fundamentales de la lógica de programación aplicadas a Shell Scripting. Aprendemos a tomar decisiones mediante condicionales, repetir procesos con bucles, modularizar código con funciones y manejar errores de ejecución.

---

## 📖 43. Estructuras Condicionales (`if`, `elif`, `else`, `case`)

Los condicionales permiten ejecutar distintas instrucciones según se cumpla o no una condición.

### A. Sintaxis con `if`, `elif` y `else`

En Bash, el bloque condicional se abre con `if [ condición ]; then` y se cierra de forma obligatoria invirtiendo la palabra: `fi`.

```bash
#!/bin/bash

# =======================================================
# Ejemplo: Estructura Condicional Base
# =======================================================

read -p "Ingresá un número: " NUMERO

if [ $NUMERO -gt 0 ]; then
    echo "El número es positivo."
elif [ $NUMERO -lt 0 ]; then
    echo "El número es negativo."
else
    echo "El número es cero."
fi

```

> ⚠️ **REGLA DE SINTAXIS:** Es obligatorio dejar un espacio en blanco después del corchete de apertura `[` y antes del corchete de cierre `]`. Escribir `if [condicion]` generará un error de sintaxis.

---

### B. Selección Múltiple con `case`

Ideal para evaluar múltiples valores posibles sobre una misma variable. Se cierra invirtiendo la palabra a `esac`.

```bash
read -p "Elige una opción (1, 2 o 3): " OPCION

case $OPCION in
    1)
        echo "Seleccionaste la Opción 1."
        ;;
    2)
        echo "Seleccionaste la Opción 2."
        ;;
    3)
        echo "Seleccionaste la Opción 3."
        ;;
    *)
        echo "Opción no válida."
        ;;
esac

```

---

## 🔍 Tabla de Operadores de Comparación

### 1. Comparación Numérica (Enteros)

| Operador | Significado | Equivalencia |
| --- | --- | --- |
| **`-eq`** | Equal | `==` (Igual a) |
| **`-ne`** | Not Equal | `!=` (Distinto de) |
| **`-gt`** | Greater Than | `>` (Mayor que) |
| **`-ge`** | Greater or Equal | `>=` (Mayor o igual) |
| **`-lt`** | Less Than | `<` (Menor que) |
| **`-le`** | Less or Equal | `<=` (Menor o igual) |

### 2. Comparación de Cadenas de Texto

| Operador | Significado |
| --- | --- |
| **`=`** / **`==`** | Las cadenas son exactamente iguales. |
| **`!=`** | Las cadenas son diferentes. |
| **`-z`** | La cadena está **vacía** (longitud 0). |
| **`-n`** | La cadena **NO está vacía** (posee contenido). |

### 3. Verificación de Archivos y Directorios

| Operador | Significado |
| --- | --- |
| **`-e`** | El archivo o directorio **existe**. |
| **`-f`** | Existe y es un **archivo regular**. |
| **`-d`** | Existe y es un **directorio**. |
| **`-r`** | Posee permisos de **lectura**. |
| **`-w`** | Posee permisos de **escritura**. |
| **`-x`** | Posee permisos de **ejecución**. |

### 4. Operadores Lógicos

| Operador | Significado |
| --- | --- |
| **`&&`** | **AND:** Se deben cumplir ambas condiciones. |
| **` |  |
| **`!`** | **NOT:** Invierte o niega el resultado de la condición. |

---

## 📖 44. Bucles e Iteraciones (`for`, `while`, `until`)

Los bucles ejecutan repetidamente un bloque de código entre las palabras reservadas `do` y `done`.

### 1. Bucle `for`

Itera sobre una lista definida de elementos o patrones de archivos:

```bash
# Iteración sobre una lista de números
for i in {1..5}; do
    echo "Número: $i"
done

# Iteración sobre archivos de la carpeta actual
for SCRIPT in *.sh; do
    echo "Encontrado script: $SCRIPT"
done

```

### 2. Bucle `while`

Ejecuta el bloque **mientras** la condición sea verdadera:

```bash
CONTADOR=1

while [ $CONTADOR -le 5 ]; do
    echo "Contador: $CONTADOR"
    CONTADOR=$((CONTADOR + 1))
done

```

### 3. Bucle `until`

Ejecuta el bloque **hasta que** la condición se vuelva verdadera (mientras sea falsa):

```bash
CONTADOR=1

until [ $CONTADOR -gt 5 ]; do
    echo "Contador Until: $CONTADOR"
    CONTADOR=$((CONTADOR + 1))
done

```

### Sentencias de Control

* **`continue`**: Omite el resto de las instrucciones de la iteración actual y salta a la siguiente.
* **`break`**: Interrumpe y finaliza la ejecución del bucle inmediatamente.

---

## 📖 45. Funciones en Bash

Las funciones encapsulan lógica reutilizable. Los argumentos que reciben dentro del bloque se capturan mediante `$1`, `$2`, etc.

```bash
#!/bin/bash

# Definición de la función
saludar_usuario() {
    local NOMBRE=$1  # 'local' restringe la variable al ámbito de la función
    echo "Hola $NOMBRE, ¡bienvenido al script!"
}

# Invocación de la función
saludar_usuario "Mariano"

```

> **💡 Códigos de retorno (`return`):**
> La palabra reservada `return` devuelve un código de estado numérico (de `0` a `255`). Por convención en sistemas Unix, `return 0` indica ejecución exitosa y valores mayores a cero indican un error.

---

## 📖 46. Manejo Básico de Errores

Cada comando ejecutado en la terminal guarda su resultado de salida en la variable especial **`$?`**:

* **`$? = 0`**: El comando se ejecutó **correctamente**.
* **`$? != 0`**: El comando falló o devolvió un **error**.

### Control de Errores Cortocircuitado

Podemos reaccionar al resultado de un comando en una sola línea usando operadores lógicos:

```bash
# Intentar copiar un archivo; si falla, ejecuta la instrucción de la derecha (||)
cp archivo_inexistente.txt /tmp/ || echo "❌ Error: El archivo especificado no existe."

# Crear directorio; si tiene éxito, ejecuta la instrucción de la derecha (&&)
mkdir /tmp/mi_carpeta && echo "✅ Directorio creado exitosamente."

```

---

## 🏋️‍♂️ 47. Laboratorio y Scripts de Prueba

Dentro de este directorio se encuentran los scripts de demostración desarrollados durante el bloque:

* 📄 **`conditionals_script.sh`**: Prácticas con condicionales `if`, `elif`, `else` y `case`.
* 📄 **`loops_script.sh`**: Demostración de iteraciones con `for`, `while` y `until`.
* 📄 **`functions_script.sh`**: Modularización mediante funciones, variables locales y parámetros.
* 📄 **`errors_script.sh`**: Captura de códigos de estado `$?` y evaluación rápida de fallos.

```

```