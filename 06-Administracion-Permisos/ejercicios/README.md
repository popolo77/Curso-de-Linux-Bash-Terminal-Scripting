# 🏋️‍♂️ Ejercicios: Administración del Sistema y Permisos

Registro de comandos ejecutados para resolver el laboratorio del Bloque 6.

## 📋 Enunciados del Bloque 6

1. **Crea un archivo y visualiza sus permisos.**
2. **Otorga permisos de ejecución solo al propietario en modo simbólico.**
3. **Cambia sus permisos a 644.**
4. **Elimina los permisos para el grupo.**
5. **Haz que sólo pueda ejecutarse por el propietario.**
6. **Crea una carpeta y dale permisos para que sólo el usuario pueda acceder.**
7. **Cámbiale el propietario a otro usuario de tu sistema (si existe y tienes permisos).**
8. **Consulta la máscara de permisos actual y calcula qué permisos por defecto tendrán los nuevos archivos.**
9. **Cambia la máscara, crea un archivo y consulta los permisos por defecto del archivo.**
10. **Utiliza un comando como superusuario.**

---

## 🛠️ Resolución de la práctica

```bash
# 1. Crea un archivo de prueba y consulta sus permisos
touch prueba_permisos.txt
ls -l prueba_permisos.txt

# 2. Otorga permisos de ejecución solo al propietario en modo simbólico
chmod u+x prueba_permisos.txt

# 3. Cambia sus permisos al modo octal 644 (rw-r--r--)
chmod 644 prueba_permisos.txt

# 4. Elimina los permisos para el grupo en modo simbólico
chmod g-r prueba_permisos.txt

# 5. Haz que sólo pueda ejecutarse por el propietario (da permisos 700 o u+rwx,go-rwx)
chmod 700 prueba_permisos.txt

# 6. Crea una carpeta privada donde sólo el propietario tenga acceso total
mkdir carpeta_privada
chmod 700 carpeta_privada

# 7. Cambia el propietario del archivo a otro usuario (requiere privilagios de administrador)
sudo chown root prueba_permisos.txt

# 8. Consulta la máscara de permisos actual (umask)
umask

# 9. Cambia la máscara temporalmente a 0022, crea un archivo y verifica sus permisos
umask 0022
touch nuevo_archivo.txt
ls -l nuevo_archivo.txt

# 10. Utiliza un comando como superusuario para actualizar la lista de paquetes
sudo apt update