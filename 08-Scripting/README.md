# 📜 Bloque 8: Introducción al Scripting

En este bloque aprendemos a convertir la consola en un entorno de automatización mediante **Shell Scripts** en Bash, pasando de ejecutar comandos individuales a programar flujos de trabajo completos.

---

## 📖 39. Fundamentos de Scripting

### 1. ¿Qué es un Shell Script?
Un **Shell Script** es un archivo de texto plano ejecutable que contiene una secuencia de comandos organizados de forma secuencial (se ejecutan línea por línea, de arriba hacia abajo) por el intérprete de Shell (`bash`).

### 2. Elementos Esenciales de un Script

#### A. El Shebang (`#!/bin/bash`)
Es **obligatorio** ubicarlo en la primera línea del archivo (sin espacios previos).
* **`#!`**: Secuencia mágica (*Shebang* o *Hashbang*).
* **`/bin/bash`**: Ruta absoluta hacia el ejecutable del intérprete de Bash.
* **Propósito:** Le indica al kernel del sistema operativo qué programa debe usar para interpretar y ejecutar las instrucciones del archivo.

#### B. Permisos de Ejecución (`chmod +x`)
Por defecto, los archivos creados en Linux no tienen permisos de ejecución. Para poder correr el script, se le deben otorgar permisos ejecutables:
```bash
chmod +x nombre_script.sh

```

#### C. Modos de Ejecución

1. **Ejecución estándar (vía directorio actual):**
```bash
./nombre_script.sh

```


2. **Invocando directamente al ejecutable de Bash:**
```bash
bash nombre_script.sh

```



---

### 3. Variables en Bash (Sintaxis Estricta)

Las variables almacenan datos en memoria durante la ejecución del script.

#### ⚠️ Regla Estricta: SIN ESPACIOS

A diferencia de otros lenguajes de programación, Bash **no tolera espacios** antes ni después del operador de asignación `=`.

```bash
# ❌ INCORRECTO (Genera error: comando no encontrado):
nombre = "Mariano"

# ✅ CORRECTO:
nombre="Mariano"

```

#### Asignación vs. Lectura

* **Para asignar:** Usamos el identificador directamente (`VARIABLE="valor"`).
* **Para leer / invocar:** Anteponemos el símbolo de dólar (`$VARIABLE` o `${VARIABLE}`).

```bash
# Ejemplo:
ESTUDIANTE="Mariano"
echo "Hola, $ESTUDIANTE!"

```

---

## 📖 40. Lectura de Datos Interactiva (`read`)

La instrucción `read` detiene la ejecución del script y aguarda a que el usuario ingrese información mediante el teclado a través de la consola.

### Modificadores Principales de `read`:

* **`read -p "Mensaje: " VARIABLE`**: Muestra una cadena explicativa (*prompt*) antes de capturar el dato.
* **`read -s -p "Clave: " PASS`**: Modo silencioso (*secret*). Oculta los caracteres en pantalla mientras el usuario tipea (ideal para passwords, tokens o claves).

---

## 📖 41. Argumentos y Parámetros Posicionales

A diferencia de `read` (que pide datos durante la corrida del programa), los **argumentos** se envían en la consola al momento de invocar el script:

```bash
./script.sh argumento1 argumento2 argumento3

```

Bash asigna estos valores a **variables especiales de posición**:

| Variable | Descripción / Función |
| --- | --- |
| **`$0`** | Nombre del archivo del script ejecutado (ej: `./script.sh`). |
| **`$1`** | **Primer argumento** enviado tras el script. |
| **`$2`** | **Segundo argumento** enviado. |
| **`$3` ... `$9**` | Argumentos del tercero al noveno. |
| **`${10}`** | Argumento en la posición 10 en adelante (requiere llaves `{}`). |
| **`$#`** | **Cantidad total** de argumentos pasados al script. |
| **`$*`** | Devuelve **todos** los argumentos juntos en una sola cadena. |
| **`$@`** | Lista **todos** los argumentos formateados como elementos independientes. |

---

## 🛠️ Scripts Prácticos de Ejemplo

### 1. Script Base de Pruebas (`08-Scripting/script.sh`)

```bash
#!/bin/bash

# =======================================================
# Curso: Linux & Shell Scripting (MoureDev)
# Bloque 8: Introducción al Scripting
# Lección 39: Fundamentos de Scripting
# =======================================================

# Definición de variables
CURSO="Linux y Bash"
ESTUDIANTE="Mariano"

echo "============================================="
echo "   Iniciando Script de Bienvenida en Bash    "
echo "============================================="
echo ""
echo "Hola, $ESTUDIANTE!"
echo "Estás estudiando el curso de: $CURSO"
echo "Ruta actual de trabajo: $(pwd)"
echo ""
echo "¡Ejecución finalizada con éxito! 🚀"

```

---

### 2. Script Interactivo con `read` y Argumentos (`08-Scripting/params_script.sh`)

```bash
#!/bin/bash

# =======================================================
# Curso: Linux & Shell Scripting (MoureDev)
# Bloque 8: Introducción al Scripting
# Lecciones 40 y 41: Read, Argumentos y Parámetros
# =======================================================

echo "============================================="
echo "    Demostración de Parámetros y Lectura     "
echo "============================================="
echo ""

# 1. Informes del sistema vía variables posicionales
echo "Script ejecutado (\$0): $0"
echo "Total de argumentos ingresados (\$#): $#"
echo "Primer argumento (\$1): $1"
echo "Segundo argumento (\$2): $2"
echo "Todos los argumentos (\$@): $@"
echo ""

# 2. Captura de datos interactiva
read -p "Ingresá tu nombre de usuario: " USUARIO
read -s -p "Ingresá tu clave secreta: " CLAVE
echo ""

echo "¡Hola $USUARIO! Datos procesados correctamente."

```

---

### 💻 Pasos de Prueba en Terminal

```bash
# 1. Conceder permisos de ejecución a los archivos
chmod +x 08-Scripting/script.sh
chmod +x 08-Scripting/params_script.sh

# 2. Ejecutar script base
./08-Scripting/script.sh

# 3. Ejecutar script con argumentos
./08-Scripting/params_script.sh Mariano Linux Bash

```

