# El principio de inversión de dependencia

El principio de inversión de dependencia (DIP) es la *D* de *SOLID*, que indica que:

1. Los módulos de alto nivel no debe depender de los módulos de mas bajo nivel, deberían depender de las abstracciones
2. Las abstracciones no deben depender de los detalles. En cambio, los detalles deben depender de abstracciones.

Los **módulos de alto nivel** son funciones, clases y paquetes que se ocupan de nuestros conceptos del mundo real

Los **módulos de bajo nivel** son código que no le importa a su organización. Para nuestros interesados no técnicos, estos conceptos de bajo nivel no son interesantes ni relevantes

Las **interfaces** encapsulan el comportamiento

### Un lugar para toda nuestra lógica empresarial: el modelo de dominio

Una de las razones mas comunes por las que nuestros diseños fallan es que la lógica empresarial se extiende por las capas de nuestra aplicación