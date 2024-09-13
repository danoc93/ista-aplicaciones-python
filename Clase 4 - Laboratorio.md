# Laboratorio 4: Explorando Github Code Spaces y acceso a datos

En este laboratorio la meta es que el estudiante explore como utilizar Github code spaces para realizar las herramientas de acceso a bases de datos en Python.

⚠️⚠️⚠️⚠️⚠️⚠️⚠️

Ya que este laboratorio requiere que creen un repositorio separado con el fin de experimentar con las herramientas, al acabar, agregar un archivo de texto con un link al nuevo repositorio dentro de la carpeta **laboratorio4** del repositorio creado en la primera clase.

⚠️⚠️⚠️⚠️⚠️⚠️⚠️

## Pasos del Laboratorio:

¡Por supuesto! Aquí tienes el diseño de laboratorio actualizado con una introducción sobre SQLite:

---


#### Introducción a SQLite

**SQLite** es una biblioteca que implementa un motor de base de datos SQL pequeño, rápido, autónomo, de alta fiabilidad. SQLite es una base de datos a base de archivos locales.

#### Parte 1: Creación y Configuración del Repositorio en GitHub

1. **Crear un NUEVO Repositorio en GitHub (diferente al de la primera clase):**

2. **Configurar el Entorno de Python:**
   - Crea un archivo `requirements.txt` y añade las dependencias necesarias, en este caso `sqlite3`.

4. **Subir Cambios a GitHub:**
   - Añade los cambios al repositorio local con `git add .`.

5. **Configurar GitHub Codespaces:**
   - Lee la [documentación de GitHub Codespaces](https://docs.github.com/es/codespaces/getting-started/quickstart) para configurar un entorno de desarrollo en la nube.

#### Parte 2: Uso de SQLite


Una vez dentro del code space, se puede trabajar directamente en el mismo, exploren usar el entorno de Visual Studio dentro del Code Space.

1. **Instalación y Configuración de SQLite:**
   - Asegúrate de que `sqlite3` esté instalado en tu entorno de Python.
   - Crea un archivo Python llamado `database.py`.

2. **Creación de una Base de Datos:**
   - En `database.py`, escribe el siguiente código para crear una base de datos y una tabla:

     ```python
     import sqlite3

     # Conexión a la base de datos (se crea si no existe)
     conn = sqlite3.connect('mi_base_de_datos.db')
     cursor = conn.cursor()

     # Crear una tabla
     cursor.execute('''
     CREATE TABLE IF NOT EXISTS usuarios (
         id INTEGER PRIMARY KEY,
         nombre TEXT NOT NULL,
         edad INTEGER NOT NULL
     )
     ''')

     # Confirmar cambios y cerrar conexión
     conn.commit()
     conn.close()
     ```

3. **Inserción y Consulta de Datos:**
   - Añade funciones para insertar y consultar datos en la base de datos:

     ```python
     def insertar_usuario(nombre, edad):
         conn = sqlite3.connect('mi_base_de_datos.db')
         cursor = conn.cursor()
         cursor.execute('INSERT INTO usuarios (nombre, edad) VALUES (?, ?)', (nombre, edad))
         conn.commit()
         conn.close()

     def consultar_usuarios():
         conn = sqlite3.connect('mi_base_de_datos.db')
         cursor = conn.cursor()
         cursor.execute('SELECT * FROM usuarios')
         usuarios = cursor.fetchall()
         conn.close()
         return usuarios
     ```

4. **Uso de las Funciones:**
   - En el mismo archivo, añade código para usar las funciones creadas:

     ```python
     # Insertar usuarios
     insertar_usuario('Alice', 30)
     insertar_usuario('Bob', 25)

     # Consultar y mostrar usuarios
     usuarios = consultar_usuarios()
     for usuario in usuarios:
         print(usuario)
     ```
5. Desde el Code Space, usar los comandos de github para subir los cambios al repositorio!

6. Agregar el archivo con un link a este repositorio dentro del Github de la primera clase, tal como lo indican las instrucciones.

7. Leer Sobre Docker y docker-compose 

https://www.redhat.com/es/topics/containers/what-is-docker

https://dev.to/ebarrioscode/que-demonios-es-docker-docker-compose-y-como-dockerizar-dotnet-core-webapi-y-sql-server-en-un-ambiente-de-desarrollo-ideal-95a
