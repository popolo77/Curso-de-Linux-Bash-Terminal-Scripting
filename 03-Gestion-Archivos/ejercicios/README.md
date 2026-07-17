# 🏋️‍♂️ Ejercicios: Gestión de Archivos y Directorios

En esta sección se encuentra el registro de los comandos utilizados para resolver el laboratorio del Bloque 3.

---

## 📋 Enunciados del Bloque 3

1. **Crea un directorio nuevo.**
2. **Elimina el directorio que acabas de crear.**
3. **Copia un archivo en el directorio actual y también haz una copia fuera de este.**
4. **Mueve un archivo del directorio actual a otra ubicación.**
5. **Cambia el nombre del archivo que acabas de mover.**
6. **Lista todos los archivos de un tipo específico usando comodines (por ejemplo, todos los `.txt`).**
7. **Elimina un directorio de manera recursiva (¡ojo con lo que borrás!).**
8. **Elimina dos archivos de un mismo tipo a la vez combinando el comando de borrado con comodines.**
9. **Utiliza el comando `tree` para ver la estructura de tus carpetas.**
10. **Busca un archivo concreto en el directorio utilizando el comando `find`.**

---

## 🛠️ Resolución de la práctica

A continuación se detalla el historial de comandos ejecutados en la terminal para resolver cada punto del laboratorio:

```bash
# 1. Crea un directorio nuevo llamado 'practica_bloque3'
mkdir practica_bloque3

# 2. Elimina el directorio que acabas de crear
rmdir practica_bloque3

# 3. Crea un archivo de prueba, lo copia al directorio actual y hace otra copia fuera
touch notas.txt
mkdir respaldo
cp notas.txt notas_copia.txt
cp notas.txt respaldo/notas_externas.txt

# 4. Mueve un archivo del directorio actual a otra ubicación (a la carpeta respaldo)
mv notas_copia.txt respaldo/

# 5. Cambia el nombre del archivo que acabas de mover (dentro de respaldo)
mv respaldo/notas_copia.txt respaldo/notas_renombrado.txt

# 6. Lista todos los archivos de tipo .txt usando comodines
ls *.txt

# 7. Elimina el directorio 'respaldo' de manera recursiva con todo su contenido
rm -r respaldo/

# 8. Crea dos archivos .log y los elimina a la vez usando comodines
touch error.log sistema.log
rm *.log

# 9. Utiliza el comando 'tree' para ver la estructura de carpetas (requiere instalación previa en algunos sistemas)
tree

# 10. Busca un archivo concreto llamado 'README.md' partiendo desde el directorio actual
find . -name "README.md"