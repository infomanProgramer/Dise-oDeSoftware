# No haga juego de palabras

Evite usar la misma palabra con dos fines distintos. Si aplica la regla de una palabra por conceptos, acabará con muchas clases que por ejemplo tengan un método add. Mientras las listas de parámetros y los valores devueltos de los distintos métodos add sean semánticamente equivalentes, no hay problema.

Por ejemplo imaginemos que tenemos el siguiente método:

~~~python
add(a, b)
~~~
Y todas hace los mismo conceptualmente
- Sumar números
- Concatenar strings
- Combina valores

En todos los casos significa combinar dos valores para producir uno nuevo

## ⚠️ El problema aparece aquí

Imagina que tienes un clase tipo colección:

~~~python
class Lista:
    def add(self, elemento):
        ...
~~~
Pero este add
- No combina dos valores
- No crea un nuevo resultado
- Solo agrega un elemento a una colección existente

Acá el significado cambia.

Antes add era:
- Combinar valores y devolver algo nuevo
- Insertar algo dentro una estructura

Son conceptos diferentes
A esto se llama juego de palabras