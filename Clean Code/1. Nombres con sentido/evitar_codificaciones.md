
# Evitar codificaciones

Ya tenemos suficientes codificaciones como para tener que añadir otras nuevas. Al codificar información de tipos o ámbitos en un nombre se dificulta la descodificación. No parece razonable que todos los nuevos empleados tengan que aprender otro lenguaje de codificación además del código con el que van a trabajar. Es una carga mental innecesaria a la hora de intentar solucionar un problema. Los nombres codificados resultan impronunciables y suelen escribirse de forma incorrecta.

No incluir información técnica dentro los nombres de variables, funciones o clases.

Por ejemplo: ante se usaba:

~~~python
strNombre = "Rafael"
intEdad = 35
lstPartidos = []
~~~

El problema con este código es que:

- Es redundante, el lenguaje ya sabe que tipo es cada varible
- Dificulta el mantenimiento, si **intEdad** deja de ser un entero y pasa a ser un decimal
- Aumenta la carga mental, los nuevos desarrolladores tienen que aprender nuevas abreviaturas
- Hace el código menos legible

En lugar de eso, se recomienda:

~~~python
nombre = "Rafael"
edad = 35
partidos = []
~~~

