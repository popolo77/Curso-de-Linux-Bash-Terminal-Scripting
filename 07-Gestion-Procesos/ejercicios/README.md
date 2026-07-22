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