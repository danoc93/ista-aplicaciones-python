# Laboratorio 3: Gestión de Dependencias de Python con Entornos Virtuales y Archivos de Requisitos

En este laboratorio la meta es que el estudiante cubra los conceptos de gestión de dependencias, entornos virtuales.

El código de este laboratorio debe ser subido a los repositorios de Github creados en el Laboratorio 1 en la carpeta **laboratorio3**

**Los laboratorios no se califican hasta el final del curso y se les asigna la nota entera al subir algo al repostorio, pero lo recomendado es tratar de cubrir todos los conceptos y ejercicios con el fin de reforzar los conocimientos.**

## Pasos del Laboratorio:

https://docs.python.org/es/3/tutorial/venv.html

Creremos dos proyectos independientes para demostrar como trabajar con versiones diferentes de la misma librería en un mismo entorno. 

Por favor subir las carpetas con el código de fuente y sus archivos de requisitos.

### 1. Introducción a los Entornos Virtuales
- Crear un entorno virtual usando `venv` en una carpeta separada para el primer proyecto.

```bash
# En Windows
mkdir project1
cd project1
python -m venv project1_env

# En macOS/Linux
mkdir project1
cd project1
python3 -m venv project1_env
```

### 2. Activación del Entorno Virtual
- Activar el entorno virtual.

```bash
# En Windows
project1_env\Scripts\activate

# En macOS/Linux
source project1_env/bin/activate
```

### 3. Instalación de Paquetes

pandas es una biblioteca de código abierto poderosa y ampliamente utilizada para el análisis y manipulación de datos en Python. Proporciona estructuras de datos como DataFrames y Series, que son esenciales para manejar datos estructurados. pandas es particularmente popular en ciencia de datos, finanzas y cualquier campo que requiera análisis de datos.

Hay dos versiones principales de pandas:

Pandas 1.x: Esta versión introdujo muchas características fundamentales y se convirtió en el estándar para la manipulación de datos en Python.

Pandas 2.x: Esta versión más reciente incluye mejoras y optimizaciones significativas, como mejor rendimiento, funcionalidad mejorada y soporte para nuevos tipos de datos. Los cambios en Pandas 2.x pueden no ser compatibles con versiones anteriores de Pandas 1.x, por lo que es importante gestionar diferentes versiones

- Instalar una versión específica de `pandas` dentro del entorno virtual.

```bash
pip install pandas==1.5
```

### 4. Creación de un Archivo de Requisitos
- Generar un archivo `requirements.txt` usando `pip freeze`.

```bash
pip freeze > requirements.txt
```

### 5. Creación de un Segundo Proyecto con Pandas 2
- Desactivar el entorno virtual actual.

```bash
# En Windows
deactivate

# En macOS/Linux
deactivate
```

- Crear y activar un nuevo entorno virtual en una carpeta separada para el segundo proyecto.

```bash
# En Windows
cd ..
mkdir project2
cd project2
python -m venv project2_env
project2_env\Scripts\activate

# En macOS/Linux
cd ..
mkdir project2
cd project2
python3 -m venv project2_env
source project2_env/bin/activate
```

- Instalar `pandas` 2.

```bash
pip install pandas==2
```

- Generar un archivo `requirements.txt` para el segundo proyecto.

```bash
pip freeze > requirements.txt
```

### 6. Uso del Archivo de Requisitos
- Usar el archivo `requirements.txt` para instalar dependencias en un nuevo entorno virtual.

```bash
# En Windows
python -m venv newenv
newenv\Scripts\activate

# En macOS/Linux
python3 -m venv newenv
source newenv/bin/activate
pip install -r requirements.txt
```

### 7. Demostración de la Importancia
- Explorar ejecutar fragmentos para cada proyecto usando diferentes versiones de `pandas`.

**Proyecto 1 (usando `pandas` 1.5):**

```python
# project1_script.py
import pandas as pd

# Imprimir la versión de pandas
print("Versión de pandas:", pd.__version__)

# Crear un DataFrame simple
df = pd.DataFrame({
    'A': [1, 2, 3],
    'B': [4, 5, 6]
})

print("Proyecto 1 - DataFrame de Pandas 1.5:")
print(df)
```

**Proyecto 2 (usando `pandas` 2):**

```python
# project2_script.py
import pandas as pd

# Imprimir la versión de pandas
print("Versión de pandas:", pd.__version__)

# Crear un DataFrame simple
df = pd.DataFrame({
    'X': [7, 8, 9],
    'Y': [10, 11, 12]
})

print("Proyecto 2 - DataFrame de Pandas 2:")
print(df)
```

Ejecuta el código y asegúrate de que las versiones correctas de pandas están siendo usadas.
