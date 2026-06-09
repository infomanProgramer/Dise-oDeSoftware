# El principio de inversión de dependencia

**Dependency Inversion Principle (DIP)** es la *D* de *SOLID*, que indica que:

1. Los módulos de alto nivel no dependen de módulos de mas bajo nivel, deberían depender de las abstracciones
2. Las abstracciones no deben depender de los detalles. Sino a la inversa

### Explicamos estas definciones

- Los **módulos de alto nivel** son funciones, clases y paquetes que se ocupan de nuestros conceptos del mundo real

- Los **módulos de bajo nivel** son código que no le importa a su a los usuarios finales ni organización.

- Las **interfaces** encapsulan el comportamiento

Los modulos de alto nivel deben ser faciles de cambiar en base a las necesidades comerciales.