# 🛡️ Bloque 6: Administración del Sistema y Permisos

En este bloque aprendemos cómo el sistema operativo gestiona la seguridad, los permisos de lectura, escritura y ejecución sobre archivos y directorios, y el uso del superusuario.

---

## 📖 28 - Tipos de permiso y usuarios

Linux divide la seguridad en tres tipos de entidades y tres niveles de acceso:

* **Usuarios:**
  * `u` (Owner / Propietario): Creador del archivo.
  * `g` (Group / Grupo): Grupo de usuarios asociados.
  * `o` (Others / Otros): El resto de los usuarios del sistema.
* **Permisos:**
  * `r` (Read / Lectura - Valor 4): Permite ver el contenido de un archivo o listar un directorio.
  * `w` (Write / Escritura - Valor 2): Permite modificar/borrar el archivo o crear/eliminar elementos en un directorio.
  * `x` (Execute / Ejecución - Valor 1): Permite ejecutar scripts o programas, y entrar a un directorio (`cd`).

---

## 📖 29 - Anatomía de los permisos (rwx)

Al ejecutar `ls -l`, los primeros 10 caracteres definen los permisos:
- El 1° carácter indica si es archivo (`-`) o directorio (`d`).
- Los 9 restantes se agrupan de a 3: **Usuario** (`rwx`), **Grupo** (`r-x`) y **Otros** (`r--`).

---

## 📖 30 - Modificación de permisos (chmod / chown)

- `chmod` **:** Modifica permisos en modo simbólico (`chmod u+x archivo.sh`) u octal (`chmod 755 archivo.sh`).
- `chown` **:** Cambia el propietario de un archivo/directorio (`chown usuario archivo.txt`).

---

## 📖 31 - Máscara de permisos (umask)

Define los permisos predeterminados al crear nuevos elementos. El valor por defecto suele restar permisos sobre el máximo teórico (666 en archivos, 777 en directorios).

---

## 📖 32 - Superusuario (sudo / su)

- `sudo` **:** Ejecuta un comando con privilegios de administrador (*root*).
- Requiere precaución ya que permite alterar configuraciones críticas del sistema.