# Realizar distinción de sentido

Los programadores se crean un problema al crear código únicamente dirigido a un compilador o interprete. 

Los nombres tienen que ser distintos no basta con añadir series numéricas a los nombre como:
~~~c#
a1
a2
a3
...
aN
~~~
Esto esta bien para el compilador, pero no para una persona ya que no comunica nada y son contrarios a los nombres intencionados

Fijémonos en el siguiente código:

~~~c#
public static void copyChars(char a1[], char a2[])
	for (int i = 0; i < a1.length; i++)
		a2[i] = a1[i];
~~~

- ¿Qué es a1?
- ¿Qué es a2?
- ¿Cuál es el origen y cual es su destino?

Esta función se lee mejor cuando se usa *sourse* o *destination* como nombres de argumentos.

~~~c#
public static void copyChars(char source[], char destination[])
	for (int i = 0; i < source.length; i++)
		destination[i] = source[i];
~~~

- Sin comentarios
- Sin explicaciones extra
- Pero ahora es claro

**Series numéricos no son nombres intencionados**

Ejemplo malo:

~~~c#
user1
user2
user3
~~~

¿Qué diferencia hay entre ellos?

Ninguna semántica

Mejor:

~~~c#
adminUser
guestUser
authenticatedUser
~~~

**Distinciones sin sentido (Product, ProductInfo, ProductData)**

Las palabras adicionales son distinciones sin sentido. Imagine que tiene las clases

~~~C#
Product
ProductInfo
ProductData
~~~

Ha creado nombres distintos, pero con el mismo significado. Esto se llama ***Distinción sin diferencia real***
### Prefijos con sentido vs sin sentido

No es incorrecto usar prefijos como *a* y *the* mientras la distinción tenga sentido, por ejemplo:

~~~c#
aCostumer //Variable local
theCostumer //Atributo de Clase
~~~

Imagine que usa *a* para variables locales y *for* para argumento de funciones. El problema aparece cuando decide invocar la variable *theZork* porque ya tiene otra variable con el nombre *zork*

~~~c#
zork
theZork
myZork
zorkObject
~~~
Esto ya es desesperación por encontrar un nombre distinto

En resumen **Realizar distinción de sentido** significa:
- No usar números para diferenciar nombres
- No agregar palabras vacías como Info, Data, Object
- No crear nombres diferentes sin diferencia conceptual
- Escribir código para humanos, no solo para compiladores