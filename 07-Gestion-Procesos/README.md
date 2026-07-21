# ⚙️ Bloque 7: Gestión de Procesos

En este bloque aprendemos cómo el sistema operativo Linux gestiona la ejecución de programas en tiempo real, la diferencia entre procesos en primer y segundo plano, el monitoreo del uso de hardware y cómo controlar o detener aplicaciones congeladas.

---

## 📖 34 - Definición y estado de los procesos

### 1. ¿Qué es un proceso?
Para entenderlo de forma didáctica:
* Un **Programa** o **Script** es un archivo estático almacenado en el disco (como una receta de cocina escrita en un papel). No consume memoria RAM ni procesador mientras esté allí.
* Un **Proceso** es ese programa cargado en la memoria RAM y ejecutándose en el procesador (el cocinero preparando la receta en tiempo real).

Cada vez que abres una terminal, ejecutas un comando o abres una aplicación, el sistema operativo le asigna un número de identificación único e irrepetible llamado **PID** (*Process ID*).

```text
  [ Programa en Disco ]  ──( Se ejecuta )──>  [ Proceso en Memoria (PID: 4120) ]

```

---

### 2. Estados de un proceso en Linux

Un proceso atraviesa distintos estados a lo largo de su ciclo de vida:

| Estado | Signo | Explicación Didáctica |
| --- | --- | --- |
| **Running** | `R` | **En ejecución:** El proceso está usando la CPU en este instante. |
| **Sleeping** | `S` | **Suspendido / Durmiendo:** Espera un evento (teclado, lectura de disco, red). Es el estado más común. |
| **Stopped** | `T` | **Detenido:** Pausado manualmente por el usuario. |
| **Zombie** | `Z` | **Zombi:** El proceso terminó, pero su proceso padre aún no ha leído su estado final. |

---

## 📖 35 - Comandos de inspección (`ps`, `top`, `htop`)

### 1. `ps` (Process Status) - Captura estática

El comando `ps` toma una "fotografía" de los procesos activos en el momento exacto en que presionas `Enter`.

El uso estándar mostrado en el curso es:

```bash
ps aux

```

#### ¿Qué significan las opciones `aux`?

* **`a`**: Muestra los procesos de **todos** los usuarios.
* **`u`**: Muestra detalles del **usuario** dueño, uso de CPU, Memoria RAM y hora de inicio.
* **`x`**: Incluye procesos que **no dependen de una terminal** (servicios del sistema).

#### 💡 Ejemplo con filtrado:

Para buscar el PID de una aplicación específica (por ejemplo, Python):

```bash
ps aux | grep python

```

---

### 2. `top` - Monitor interactivo

`top` abre una pantalla dinámica que actualiza en tiempo real el consumo de recursos de la máquina.

```bash
top

```

#### Teclas interactivas dentro de `top`:

* **`P`** (Shift + p): Ordena los procesos por consumo de **CPU**.
* **`M`** (Shift + m): Ordena los procesos por consumo de **Memoria RAM**.
* **`k`**: Permite cerrar un proceso introduciendo su PID.
* **`q`**: **Salir** del monitor.

---

### 3. `htop` - Monitor avanzado e interactivo

Es una versión evolucionada y visual de `top`. Muestra barras de colores por cada núcleo del procesador, uso de RAM y permite navegar con las flechas o ratón.

```bash
htop

```

---

## 📖 36 - Gestión y finalización de procesos (`kill`, `killall`)

Cuando una aplicación no responde o consume recursos de manera desmedida, le enviamos una señal (*signal*) para cerrarla.

### 1. `kill` (Por PID)

Envía una señal al proceso utilizando su número de PID.

#### A. Señal `SIGTERM` (Señal 15 - Por defecto):

Es una solicitud amigable de cierre. Permite al programa guardar cambios antes de salir.

```bash
kill 4521

```

#### B. Señal `SIGKILL` (Señal 9 - Cierre forzado):

Obliga al Kernel de Linux a destruir el proceso de forma inmediata.

```bash
kill -9 4521

```

---

### 2. `killall` (Por nombre)

Permite cerrar todas las instancias de un programa buscando directamente por su nombre exacto:

```bash
killall firefox

```

---

## 📖 37 - Trabajos en primer y segundo plano (`bg`, `fg`, `jobs`, `&`)

Por defecto, los comandos se ejecutan en **primer plano** (*foreground*), bloqueando la consola hasta terminar.

### 1. Operador `&` (Ejecución en segundo plano)

Al añadir un `&` al final de un comando, este se ejecuta en **segundo plano** (*background*) dejando la terminal libre.

```bash
pc@DESKTOP:~$ sleep 300 &
[1] 5823

```

* **`[1]`**: Identificador del trabajo (*Job ID*).
* **`5823`**: Número de PID en el sistema.

---

### 2. Gestión de trabajos (`jobs`, `bg`, `fg`)

* **`jobs`**: Muestra los trabajos en segundo plano en la sesión actual.
* **`Ctrl + Z`**: Pausa el proceso actual que está en primer plano.
* **`bg %ID`**: Reanuda en **segundo plano** un proceso pausado.
* **`fg %ID`**: Trae de vuelta al **primer plano** un proceso en segundo plano.

```

---

### 2️⃣ Archivo del Laboratorio Práctico
📁 **Ruta:** `07-Gestion-Procesos/ejercicios/README.md`

```markdown
# 🏋️‍♂️ Ejercicios: Gestión de Procesos

Registro de comandos y pasos utilizados para resolver el laboratorio práctico del Bloque 7.

## 📋 Enunciados del Bloque 7

1. **Visualiza los procesos en ejecución de tu usuario.**
2. **Usa `top` o `htop` para ordenar los procesos por uso de CPU o memoria.**
3. **Ejecuta un proceso en segundo plano (por ejemplo, `sleep 100 &`).**
4. **Comprueba que el proceso está corriendo con `jobs` o `ps`.**
5. **Pasa el proceso a primer plano y vuélvelo a enviar a segundo plano.**
6. **Mata el proceso utilizando su PID.**
7. **Crea varios procesos iguales en segundo plano y ciérralos todos a la vez con `killall`.**

---

## 🛠️ Resolución de la práctica

### Pasos ejecutados en la consola:

1. **Visualizar procesos del usuario actual:**
   ```bash
   ps u

```

2. **Monitoreo interactivo:**
```bash
top

```


* *Acción:* Se presionó `M` para ordenar por consumo de memoria RAM y luego `q` para salir.


3. **Ejecutar proceso en segundo plano:**
```bash
sleep 100 &

```


4. **Verificar el trabajo activo:**
```bash
jobs

```


5. **Alternar entre primer y segundo plano:**
```bash
# Traer al primer plano
fg %1

# Pausar con la combinación de teclas: Ctrl + Z

# Reanudar en segundo plano
bg %1

```


6. **Finalizar proceso por PID:**
```bash
# Consultar el PID
ps aux | grep sleep

# Terminar el proceso
kill <NÚMERO_DE_PID>

```


7. **Crear múltiples instancias y cerrar con `killall`:**
```bash
sleep 300 &
sleep 300 &
sleep 300 &

# Finalizar todas las instancias de sleep
killall sleep

```



```

```