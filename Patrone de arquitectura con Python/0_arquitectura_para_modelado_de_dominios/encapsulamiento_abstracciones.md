# Encapsulamiento y abstracciones

El termino Encapsulamiento cubre dos ideas estrechamente relacionadas:

- Simplificar el comportamiento (que una función de 100 líneas convertirla en una de 10 líneas)
- Ocultar datos

Veamos los dos siguientes fragmentos de código de Python:

~~~python
import json
from urllib.request import urlopen
from urllib.parse import urlencode

params = dict(q='Salchichas', format='json')

handle = urlopen(
    'https://api.duckduckgo.com/?' + urlencode(params)
)

raw_text = handle.read().decode('utf8')
analizado = json.loads(raw_text)
resultados = analizado['RelatedTopics']

for r in resultados:
    if 'Text' in r:
        print(r['FirstURL'] + ' - ' + r['Text'])
~~~

~~~python
import requests

params = dict(q='Salchichas', format='json')

analizado = requests.get(
    'https://api.duckduckgo.com/',
    params=params
).json()

resultados = analizado['RelatedTopics']

for r in resultados:
    if 'Text' in r:
        print(r['FirstURL'] + ' - ' + r['Text'])
~~~

Ambos códigos hacen lo mismo envian valores codificados en forma a una URL para usar una API de motor de búesqueda. Pero el segundo es mas facil de comprender por que opera a un nivel mas alto de abstracción.

Se puede dar un paso mas alla identificando y nombrando la tarea que queremos que el código realice por nosotros y usando una abstracción de nivel aún mas alto para hacerlo mas explicito

~~~python
import duckduckgo

for r in duckduckgo.query('Salchichas').results:
    print(r.url + ' - ' + r.text)
~~~

>*Encapsular el comportamiento mediante el uso de abstracciones es una herramienta poderosa para hacer que el código se más expresivo, mas comprobable y mas fácil de mantener.*

En la literatura del mundo orientado a objetos OO, una de las caracterizaciones clásicas de este enfoque se denomina **Diseño impulsado por la responsabilidad**, utiliza las palabras funciones y responsabilidades en lugar de tareas.  El punto principal es pensar en el código en términos de comportamiento, más que en términos de datos o algoritmos.

*En un leguaje OO tradicional como Java o C#, puedes usar una clase abstracta (ABC), o una interfaz para definir una abstracción. En Python puedes usar ABC, pero también puedes confiar felizmente en la* ***Tipificación Pato***