# ⏰ Bloque 10: Automatización y Cron Jobs

## 📖 48 - Cron Jobs y Tareas Programadas

### 1. ¿Qué es Cron y Crontab?

* **Cron:** Es un demonio (*daemon*) o servicio del sistema operativo en Linux/Unix que corre en segundo plano de forma permanente. Su trabajo es revisar cada minuto si hay tareas programadas para ejecutar.
* **Crontab (*Cron Table*):** Es un archivo de texto donde guardamos el listado de reglas e instrucciones que le dicen a Cron **qué comando/script ejecutar** y **en qué momento exacto**.

---

### 2. Comandos Básicos de Gestión de Crontab

| Comando | Descripción |
| --- | --- |
| **`crontab -l`** | **Listar:** Muestra las tareas programadas activas para el usuario actual. |
| **`crontab -e`** | **Editar:** Abre el archivo de configuración en el editor por defecto (Nano/Vim) para agregar o modificar tareas. |
| **`crontab -r`** | **Remover:** Borra todas las tareas programadas del usuario (**¡usar con cuidado!**). |

---

### 3. Anatomía y Sintaxis de una Regla Cron

Cada línea dentro de un archivo `crontab` se compone de **5 campos de tiempo** seguidos del **comando o script a ejecutar**:

```text
┌───────────── minuto (0 - 59)
│ ┌───────────── hora (0 - 23)
│ │ ┌───────────── día del mes (1 - 31)
│ │ │ ┌───────────── mes (1 - 12)
│ │ │ │ ┌───────────── día de la semana (0 - 6) [0 = Domingo]
│ │ │ │ │
* * * * *  /ruta/absoluta/a/tu/script.sh

```

#### Símbolos Especiales:

* **`*` (Asterisco):** Significa *"todos"* (todos los minutos, todas las horas, etc.).
* **`,` (Coma):** Permite especificar una lista de valores. Ej: `0 9,18 * * *` (a las 9:00 y a las 18:00).
* **`-` (Guion):** Permite especificar un rango. Ej: `0 9 * * 1-5` (de Lunes a Viernes a las 9:00).
* **`/*` (Barra / Intervalos):** Especifica saltos o incrementos. Ej: `*/15 * * * *` (cada 15 minutos).

---

### 💡 Ejemplos Prácticos de Sintaxis Cron

| Expresión Cron | Significado |
| --- | --- |
| **`* * * * *`** | Ejecutar **cada minuto**. |
| **`*/5 * * * *`** | Ejecutar **cada 5 minutos**. |
| **`0 2 * * *`** | Ejecutar todos los días a las **2:00 AM**. |
| **`30 14 * * 1`** | Ejecutar todos los **Lunes a las 14:30 hs**. |
| **`0 0 1 * *`** | Ejecutar el **primer día de cada mes** a la medianoche. |

---

### ⚠️ Regla Crítica para Cron Jobs: ¡Rutas Absolutas y Redirección!

1. **Rutas Absolutas:** Cron no conoce el directorio de trabajo donde estás parado ni las variables de entorno habituales. **Siempre usá rutas completas**, tanto para el intérprete como para el script y archivos de salida:
```bash
# ✅ CORRECTO:
* * * * * /bin/bash /home/mariano/scripts/backup.sh

```


2. **Redirección de Salida (Logs):** Al ejecutarse de fondo, Cron no tiene una pantalla donde imprimir los `echo`. Conviene redirigir la salida a un archivo `.log` para verificar que funcionó:
```bash
* * * * * /home/mariano/scripts/backup.sh >> /home/mariano/scripts/backup.log 2>&1

```



---

## 🛠️ Código del Ejemplo Práctico (`10-Cron-Jobs/script_cron.sh`)

Podés crear este script sencillo de prueba dentro de `10-Cron-Jobs/`:

```bash
#!/bin/bash

# =======================================================
# Curso: Linux & Shell Scripting (MoureDev)
# Bloque 10: Automatización y Cron Jobs
# Lección 48: Script de Prueba para Cron
# =======================================================

LOG_FILE="/home/mariano/Curso-de-Linux-Bash-Terminal-Scripting/10-Cron-Jobs/cron_ejecucion.log"

echo "Cron ejecutado con éxito el: $(date)" >> "$LOG_FILE"

```

---

### 🧪 Paso a Paso para Probarlo:

1. Concedele permisos de ejecución:
```bash
chmod +x 10-Cron-Jobs/script_cron.sh

```


2. Abrí tu crontab:
```bash
crontab -e

```


3. Agregá la siguiente línea al final del archivo (ajustando a tu ruta exacta de sistema) para que corra cada minuto:
```text
* * * * * /home/mariano/Curso-de-Linux-Bash-Terminal-Scripting/10-Cron-Jobs/script_cron.sh

```


4. Guardá el archivo y esperá 2 o 3 minutos. Podés verificar cómo se escribe automáticamente con:
```bash
cat 10-Cron-Jobs/cron_ejecucion.log

```



