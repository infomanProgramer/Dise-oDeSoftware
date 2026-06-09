**¿Por qué nuestros diseños salen mal?**

Los sistemas de software tienden al caos.
Los sistemas de software caóticos se caracterizan por una similitud de funciones: Controladores de API que tienen conocimiento del dominio y envían correos y realizan registros.
Clases de negocios que no realizan cálculos pero realizan operaciones de E/S y todo acoplado a todo lo demás.

Una gran bola de barro es el estado natural del software de la misma manera que la naturaleza salvaje es el estado natural de su jardín, Se necesita energía y dirección para evitar el colapso.
## Encapsulamiento y abstracciones

El termino Encapsulamiento cubre dos ideas estrechamente relacionadas:

- Simplificar el comportamiento (que una función de 100 líneas convertirla en una de 10 líneas)
- Ocultar datos

*Encapsular el comportamiento mediante el uso de abstracciones es una herramienta poderosa para hacer que el código se más expresivo, mas comprobable y mas fácil de mantener.*

En la literatura del mundo orientado a objetos OO, una de las caracterizaciones clásicas de este enfoque se denomina **Diseño impulsado por la responsabilidad**, utiliza las palabras funciones y responsabilidades en lugar de tareas.  El punto principal es pensar en el código en términos de comportamiento, más que en términos de datos o algoritmos.

*En un leguaje OO tradicional como Java o C#, puedes usar una clase abstracta (ABC), o una interfaz para definir una abstracción. En Python puedes usar ABC, pero también puedes confiar felizmente en la* ***Tipificación Pato***
## Capas

Debemos prestar atención a la interacción de nuestros objetos y funciones. Cuando una función u objeto utiliza otro, decimos que uno depende del otro. Estas dependencias forman una especie de red o grafico de nodos. Cambiar un nodo del gráfico se vuelve difícil por que tiene el potencial de afectar muchas otras partes del sistema. ***Las arquitecturas en capas son una forma de abordar este problema*** 

En arquitecturas de capas, dividimos nuestro código en categorías o roles discretos e introducimos reglas sobre que categorías del código se pueden llamar entre si.

Uno de los ejemplos mas comunes es la arquitectura de tres capas:

![[Pasted image 20260608224651.png]]

En este modelo tenemos componentes como la **capa de presentación** (interfaz de usuario) que pueden ser:
- Pagina Web
- API
- Linea de comandos

En la **capa de lógica** de negocio tenemos las reglas comerciales y nuestros flujos de trabajo
Finalmente tenemos la capa de base de datos que es responsable de almacenar y recuperar datos

Durante este libro daremos vuelta sistemáticamente a este modelo obedeciendo un principio simple.

## El principio de inversión de dependencia

El principio de inversión de dependencia (DIP) es la *D* de *SOLID*, que indica que:

1. Los módulos de alto nivel no debe depender de los módulos de mas bajo nivel, deberían depender de las abstracciones
2. Las abstracciones no deben depender de los detalles. En cambio, los detalles deben depender de abstracciones.

Los **módulos de alto nivel** son funciones, clases y paquetes que se ocupan de nuestros conceptos del mundo real

Los **módulos de bajo nivel** son código que no le importa a su organización. Para nuestros interesados no técnicos, estos conceptos de bajo nivel no son interesantes ni relevantes

Las **interfaces** encapsulan el comportamiento
## Un lugar para toda nuestra lógica empresarial: el modelo de dominio

Una de las razones mas comunes por las que nuestros diseños fallan es que la lógica empresarial se extiende por las capas de nuestra aplicación





