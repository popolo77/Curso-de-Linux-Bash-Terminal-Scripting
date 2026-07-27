# 🏋️‍♂️ Ejercicios Resueltos - Bloque 9: Lógica y Control de Flujo

Este directorio contiene las soluciones prácticas para las lecciones del **Bloque 9**, cubriendo el uso de estructuras condicionales (`if`, `elif`, `else`, `case`), bucles (`for`, `while`), funciones con parámetros y valores de retorno, y manejo de errores con operadores lógicos.

---

## 📋 Lista de Ejercicios y Enunciados

### 1. Evaluación Numérica (`ejercicio1.sh`)
> **Consigna:** Crear un script que pida un número al usuario y muestre si es **positivo**, **negativo** o **cero** utilizando `if`, `elif` y `else`.
```bash
#!/bin/bash

read -p "Ingresá un número: " NUMERO

if [ $NUMERO -gt 0 ]; then
    echo "El número $NUMERO es positivo."
elif [ $NUMERO -lt 0 ]; then
    echo "El número $NUMERO es negativo."
else
    echo "El número ingresado es cero."
fi

```

---

### 2. Comparación de Números (`ejercicio2.sh`)

> **Consigna:** Solicitar al usuario dos números y mostrar cuál es mayor, cuál es menor o si ambos son iguales.

```bash
#!/bin/bash

read -p "Ingresá el primer número: " N1
read -p "Ingresá el segundo número: " N2

if [ $N1 -gt$N2 ]; then
    echo "$N1 es mayor que$N2."
elif [ $N2 -gt$N1 ]; then
    echo "$N2 es mayor que$N1."
else
    echo "Ambos números son iguales ($N1)."
fi

```

---

### 3. Menú Interactivo con `case` (`ejercicio3.sh`)

> **Consigna:** Crear un menú interactivo con 3 opciones que ejecute una acción distinta según la elección del usuario.

```bash
#!/bin/bash

echo "=== MENÚ DE OPCIONES ==="
echo "1) Mostrar fecha y hora"
echo "2) Mostrar directorio actual"
echo "3) Mostrar usuario del sistema"
read -p "Elige una opción (1-3): " OPCION

case $OPCION in
    1)
        echo "Fecha y hora: $(date)"
        ;;
    2)
        echo "Directorio actual: $(pwd)"
        ;;
    3)
        echo "Usuario activo: $(whoami)"
        ;;
    *)
        echo "❌ Opción no válida."
        ;;
esac

```

---

### 4. Bucle `for` del 1 al 10 (`ejercicio4.sh`)

> **Consigna:** Mostrar los números del 1 al 10 utilizando un bucle `for`.

```bash
#!/bin/bash

echo "Contando del 1 al 10 con bucle 'for':"
for i in {1..10}; do
    echo "Número: $i"
done

```

---

### 5. Contador Acumulativo con `while` (`ejercicio5.sh`)

> **Consigna:** Crear un script que pida números al usuario hasta que ingrese el número `0`. Al finalizar, debe mostrar cuántos números se ingresaron en total.

```bash
#!/bin/bash

CONTADOR=0
NUMERO=-1

echo "Ingresá números (ingresá '0' para terminar):"

while [ $NUMERO -ne 0 ]; do
    read -p "Número: " NUMERO
    if [ $NUMERO -ne 0 ]; then
        CONTADOR=$((CONTADOR + 1))
    fi
done

echo "Ingresaste un total de $CONTADOR números."

```

---

### 6. Control de Bucles (`continue` y `break`) (`ejercicio6.sh`)

> **Consigna:** Mostrar los números del 1 al 10, pero **saltando el 5** (usando `continue`) y **deteniendo el bucle en el 8** (usando `break`).

```bash
#!/bin/bash

for i in {1..10}; do
    if [ $i -eq 5 ]; then
        continue # Salta la impresión del 5
    fi
    
    if [ $i -eq 8 ]; then
        echo "Se alcanzó el número 8. Deteniendo bucle con break."
        break # Cancela el bucle por completo
    fi

    echo "Número: $i"
done

```

---

### 7. Función con Argumentos (`ejercicio7.sh`)

> **Consigna:** Crear una función llamada `saludar` que reciba un nombre como argumento y muestre un mensaje de bienvenida.

```bash
#!/bin/bash

saludar() {
    local NOMBRE=$1
    echo "Hola $NOMBRE, ¡bienvenido al script!"
}

read -p "Ingresá tu nombre: " USUARIO
saludar "$USUARIO"

```

---

### 8. Función de Suma con Retorno (`ejercicio8.sh`)

> **Consigna:** Crear una función que reciba dos números, calcule su suma y la devuelva mediante un código de retorno (`return`), mostrándola en el script principal.

```bash
#!/bin/bash

sumar() {
    local RESULTADO=$(( $1 + $2 ))
    return $RESULTADO
}

sumar 12 8
SUMA=$? # Captura el código de salida retornado por la última función

echo "El resultado de la suma es: $SUMA"

```

---

### 9. Captura y Manejo de Errores (`ejercicio9.sh`)

> **Consigna:** Intentar copiar un archivo inexistente y capturar el fallo mostrando un mensaje de error personalizado mediante el operador lógico `||`.

```bash
#!/bin/bash

ARCHIVO="archivo_inexistente.txt"

# Intenta la copia; si falla (código != 0), ejecuta la instrucción de la derecha
cp "$ARCHIVO" /tmp/ 2>/dev/null || echo "❌ Error: No se pudo copiar '$ARCHIVO' porque el archivo no existe."

```

---

### 10. Script Documentado e Iterativo (`ejercicio10.sh`)

> **Consigna:** Crear un script documentado con autor y fecha que liste todos los archivos `.sh` del directorio actual.

```bash
#!/bin/bash

# =======================================================
# Autor: Mariano
# Fecha: 2026
# Descripción: Script documentado que itera sobre los .sh
# =======================================================

echo "Buscando archivos de script (.sh) en el directorio actual..."

for SCRIPT in *.sh; do
    if [ -f "$SCRIPT" ]; then
        echo "📄 Encontrado: $SCRIPT"
    fi
done

```

---

## 🛠️ Instrucciones de Ejecución

1. Otorgar permisos de ejecución a todos los scripts:
```bash
chmod +x *.sh

```


2. Ejecutar individualmente cualquiera de los ejercicios:
```bash
./ejercicio1.sh
./ejercicio3.sh

