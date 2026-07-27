# 🏋️‍♂️ Ejercicios Resueltos - Bloque 10: Automatización y Cron Jobs

Este directorio contiene las soluciones y configuraciones para los ejercicios prácticos sobre programación de tareas automatizadas con **Cron** y **Crontab**.

> **Nota:** Para probar estos ejercicios en tu sistema, asegúrate de reemplazar `/ruta/absoluta` por la ubicación real de tu proyecto en el disco.

---

## 📋 Lista de Ejercicios y Expresiones Cron

### 1. Ejecución Minutal (`ejercicio1.sh`)
> **Consigna:** Crear un script que guarde la fecha y hora actual en un archivo `ejecucion.log` y programarlo con Cron para que corra **cada minuto**.

**Script (`ejercicio1.sh`):**
```bash
#!/bin/bash
echo "Ejecutado el: $(date)" >> /ruta/absoluta/ejecucion.log

```

**Regla Crontab:**

```text
* * * * * /ruta/absoluta/ejercicio1.sh

```

---

### 2. Ejecución Cada 5 Minutos (`ejercicio2.sh`)

> **Consigna:** Crear un script que escriba `"Hola desde Cron"` en un archivo log y configurarlo para que se ejecute **cada 5 minutos**.

**Script (`ejercicio2.sh`):**

```bash
#!/bin/bash
echo "Hola desde Cron - $(date)" >> /ruta/absoluta/hola_cron.log

```

**Regla Crontab:**

```text
*/5 * * * * /ruta/absoluta/ejercicio2.sh

```

---

### 3. Backup Diario a las 2 AM (`ejercicio3.sh`)

> **Consigna:** Crear un script de respaldo que comprima una carpeta en un archivo `.tar.gz` con la fecha actual y programarlo para ejecutarse **todos los días a las 02:00 AM**.

**Script (`ejercicio3.sh`):**

```bash
#!/bin/bash
FECHA=$(date +%Y-%m-%d)
tar -czf /ruta/absoluta/backup_$FECHA.tar.gz /ruta/absoluta/carpetadatos/

```

**Regla Crontab:**

```text
0 2 * * * /ruta/absoluta/ejercicio3.sh

```

---

### 4. Limpieza Semanal los Domingos a Medianoche (`ejercicio4.sh`)

> **Consigna:** Crear un script que borre todos los archivos `.log` de una carpeta temporal y programarlo para que corra **todos los domingos a la medianoche (00:00 hs)**.

**Script (`ejercicio4.sh`):**

```bash
#!/bin/bash
rm -f /tmp/logs/*.log

```

**Regla Crontab:**

```text
0 0 * * 0 /ruta/absoluta/ejercicio4.sh

```

---

### 5. Reporte Horario de Trabajo (`ejercicio5.sh`)

> **Consigna:** Programar un script que escriba la hora actual cada hora, únicamente dentro de la jornada laboral de **9:00 a 17:00 hs**.

**Script (`ejercicio5.sh`):**

```bash
#!/bin/bash
echo "Reporte horario: $(date)" >> /ruta/absoluta/jornada.log

```

**Regla Crontab:**

```text
0 9-17 * * * /ruta/absoluta/ejercicio5.sh

```

---

### 6. Notificación de Días Específicos (`ejercicio6.sh`)

> **Consigna:** Configurar una tarea automatizada para que imprima `"Hoy toca practicar"` únicamente los días **Lunes, Miércoles y Viernes a las 8:00 AM**.

**Script (`ejercicio6.sh`):**

```bash
#!/bin/bash
echo "Hoy toca practicar Bash y Linux 🚀" >> /ruta/absoluta/recordatorio.log

```

**Regla Crontab:**

```text
0 8 * * 1,3,5 /ruta/absoluta/ejercicio6.sh

```

---

### 7. Redirección de Errores a Log (`ejercicio7.sh`)

> **Consigna:** Configurar una regla en Crontab para que tanto la **salida estándar (`stdout`)** como los **errores (`stderr`)** de un script se guarden en un archivo de log unificado.

**Regla Crontab:**

```text
*/10 * * * * /ruta/absoluta/ejercicio7.sh >> /ruta/absoluta/salida.log 2>&1

```

---

### 8. Ejecución Mensual el Día 1 (`ejercicio8.sh`)

> **Consigna:** Crear un script que genere un reporte mensual y programarlo para que se ejecute el **primer día de cada mes a las 00:00 hs**.

**Script (`ejercicio8.sh`):**

```bash
#!/bin/bash
echo "--- Reporte Mensual del $(date +%B) ---" > /ruta/absoluta/reporte_mensual.log

```

**Regla Crontab:**

```text
0 0 1 * * /ruta/absoluta/ejercicio8.sh

```

---

### 9. Control de Entorno y Variables en Cron (`ejercicio9.sh`)

> **Consigna:** Probar la falta de entorno en Cron declarando la variable `PATH` explícitamente en el archivo Crontab o usando rutas absolutas dentro del script.

**Regla Crontab (con definición de PATH):**

```text
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
0 12 * * * /ruta/absoluta/ejercicio9.sh

```

---

### 10. Verificación de Logs del Sistema (`ejercicio10.sh`)

> **Consigna:** Comprobar desde la consola que las tareas programadas en Cron se están ejecutando leyendo los logs del sistema con `grep`.

**Comandos de verificación:**

```bash
# En sistemas basados en Debian/Ubuntu:
grep CRON /var/log/syslog

# O bien usando journalctl (en distribuciones con systemd):
sudo journalctl -u cron --since "1 hour ago"

```

---

## 🛠️ Cómo Cargar estas Reglas en tu Sistema

1. Edita tu tabla de tareas activas:
```bash
crontab -e

```


2. Agrega la línea de la regla deseada al final del archivo guardando con el editor (Nano/Vim).
3. Verifica que la tarea quedó registrada correctamente:
```bash
crontab -l

