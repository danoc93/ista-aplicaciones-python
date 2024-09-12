# Laboratorio 2

En este laboratorio la meta es que el estudiante cubra los conceptos de modulos, guías de estilo cubiertos en las clases.

El código de este laboratorio debe ser subido a los repositorios de Github creados en el Laboratorio 1 en la carpeta **laboratorio2**

**Los laboratorios no se califican hasta el final del curso y se les asigna la nota entera al subir algo al repostorio, pero lo recomendado es tratar de cubrir todos los conceptos y ejercicios con el fin de reforzar los conocimientos.**

## Leer la guía de estilo de Python y Google para recomendaciones de código
[https://peps.python.org/pep-0008/](https://peps.python.org/pep-0008/)

[https://google.github.io/styleguide/pyguide.html
](https://google.github.io/styleguide/pyguide.html)

## Instalar Python3.12 o cualquier version mayor a 3.5

Si ya lo tienen instalado, saltar este paso.

## Crear un paquete llamado instituto con módulos estudiante y clase

1. En el módulo **estudiante** debe tener una variable con un **diccionario** de estudiantes y materias:

Por ejemplo el diccionario puede tener la siguiente información:

- Daniel: [Matematica, Computacion]
- Maria: [Matematica, Fisica]

2. El módulo **estudiante** debe tener una función devolver_materias que acceda a este diccionario y devuelva la lista de materias para un estudiante:

Con el ejemplo de arriba, el resultado es el siguiente:

devolver_materias(Daniel) -> [Matematica, Computacion]

devolver_materias(Maria) -> [Matematica, Fisica]

3. El módulo **clase** debe tener una función que determine si un estudiante esta registrado en una clase, debe importar devolver_materias del otro módulo.

Con el ejemplo de arriba, el resultado es el siguiente:

estudiante_registrado_en_materia("Daniel", "Matematica") -> True

estudiante_registrado_en_materia("Daniel", "Biologia") -> False

4. En caso de que el estudiante no exista en el diccionario, Python puede lanzar una excepción genérica. Captúrela e imprima un mensaje más útil.
 

## Leer el documento de anotaciones de tipado en Python

https://docs.python.org/3/library/typing.html
https://dev.to/rohaquinlop/que-son-los-type-hints-en-python-mejorar-la-calidad-de-tu-codigo-y-hazlo-mas-legible-5e99

## Ajustar el código para usar anotaciones de tipado

Basado en el documento anterior y la presentación, intente agregar anotaciones de tipo a sus funciones y variables.
 
