# Laboratorio 5: Servicios web en flask y pipelines CI/CD con CircleCI

En este laboratorio la meta es que el estudiante explore como utilizar flask para crear sus propios sevicios web, y explore herramientas de automatización de la cadena de integración y emisión usando CircleCI.

⚠️⚠️⚠️⚠️⚠️⚠️⚠️

Ya que este laboratorio requiere que creen un repositorio separado con el fin de experimentar con las herramientas, al acabar, agregar un archivo de texto con un link al nuevo repositorio dentro de la carpeta **laboratorio5** del repositorio creado en la primera clase.

⚠️⚠️⚠️⚠️⚠️⚠️⚠️

## Pasos del Laboratorio:

Empezar por crear un repositorio nuevo para su proyecto. Se puede trabajar localmente o usando Github CodeSpaces como se cubrió en el laboratorio anterior.

#### Introducción

En este laboratorio, aprenderás a crear una aplicación web más compleja usando Flask y a configurar un pipeline de integración continua (CI) con CircleCI. Utilizaremos herramientas como **Black** para formateo de código y **Mypy** para verificación de tipos. Puedes realizar este laboratorio en tu máquina local o utilizando **GitHub Codespaces**.

#### ¿Qué es Flask?

**Flask** es un microframework para Python que permite desarrollar aplicaciones web de manera rápida y sencilla. Es ligero y flexible, lo que lo hace ideal para proyectos pequeños y medianos.

#### ¿Qué es CircleCI?

**CircleCI** es una plataforma de integración continua y entrega continua (CI/CD) que automatiza el proceso de construcción, prueba y despliegue de aplicaciones de software. Permite a los equipos de desarrollo integrar y entregar código de manera más rápida y eficiente.

### Paso 1: Crear una Aplicación Web Compleja con Flask

1. **Instalar Flask**:
   ```bash
   pip install Flask
   ```

2. **Crear la Estructura del Proyecto**:
   ```bash
   mkdir flask_app
   cd flask_app
   mkdir templates static
   touch app.py
   ```

3. **Configurar la Aplicación Flask**:
   ```python
   from flask import Flask, render_template

   app = Flask(__name__)

   @app.route('/')
   def home():
       return render_template('home.html')

   @app.route('/about')
   def about():
       return render_template('about.html')

   if __name__ == '__main__':
       app.run(debug=True)
   ```

4. **Crear Plantillas HTML**:
   - **templates/home.html**:
     ```html
     <!DOCTYPE html>
     <html lang="en">
     <head>
         <meta charset="UTF-8">
         <meta name="viewport" content="width=device-width, initial-scale=1.0">
         <title>Home</title>
     </head>
     <body>
         <h1>Página de Inicio</h1>
         <a href="{{ url_for('acercade') }}">Acerca de</a>
     </body>
     </html>
     ```

   - **templates/acercade.html**:
     ```html
     <!DOCTYPE html>
     <html lang="en">
     <head>
         <meta charset="UTF-8">
         <meta name="viewport" content="width=device-width, initial-scale=1.0">
         <title>Acerca de</title>
     </head>
     <body>
         <h1>Me llamo XXX</h1>
         <a href="{{ url_for('home') }}">Inicio</a>
     </body>
     </html>
     ```

### Paso 2: Configurar CI con CircleCI

1. **Crear un Archivo de Configuración de CircleCI**:
   - Dentro del directorio del proyecto, crea una carpeta `.circleci` y un archivo `config.yml`:
     ```bash
     mkdir .circleci
     touch .circleci/config.yml
     ```

2. **Escribir la Configuración de CircleCI**:

Revisar la documentación de CircleCI para la información más actualizada sobre la configuración.

   ```yaml
   version: 2.1

   jobs:
     test:
       docker:
         - image: circleci/python:3.8
       steps:
         - checkout
         - run:
             name: Instalar dependencias
             command: |
               python -m venv venv
               . venv/bin/activate
               pip install -r requirements.txt
         - run:
             name: Ejecutar Black
             command: |
               . venv/bin/activate
               black --check .
         - run:
             name: Ejecutar Mypy
             command: |
               . venv/bin/activate
               mypy app.py

   workflows:
     version: 2
     test:
       jobs:
         - test
   ```

4. **Agregar Dependencias a `requirements.txt`**:
   ```txt
   Flask
   black
   mypy
   ```

5. **Configurar el Proyecto en CircleCI**:
   - Ve a [CircleCI](https://circleci.com/) y conecta tu repositorio de GitHub.
   - CircleCI detectará automáticamente el archivo `config.yml` y comenzará a ejecutar el pipeline.


### Resumen

: [CircleCI Overview](https://circleci.com/docs/about-circleci/)

: [Continuous Integration and Delivery - CircleCI](https://circleci.com/)

: [What is Flask Python](https://pythonbasics.org/what-is-flask-python/)

: [Flask Tutorial - GeeksforGeeks](https://www.geeksforgeeks.org/flask-tutorial/)
