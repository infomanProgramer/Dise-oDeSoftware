# Introducción

La dirección de las dependencias dentro de una aplicación debe ir hacia las abstracciones, no hacia detalles de la implementación. La mayoría de las aplicaciones están escritas de forma que la dependencia en **Tiempo de Compilación** fluye en la misma dirección que la **Ejecución en Tiempo de Ejecución**.

Esto tiene sentido a nivel de **ejecución** (cuando el programa corre), pero si las capas superiores dependen **directamente** de las clases concretas de las capas inferiores (como DAOs, repositorios, etc.), entonces **las decisiones importantes del dominio están acopladas a detalles técnicos.**

**Ejemplo**

Si la clase A llama a un método de la clase B y B llama a un método de la clase C, entonces el tiempo de compilación de A dependerá de B y B dependerá de la clase C

![[Pasted image 20250625095651.png]]Aplicando el principio de **Inversión de Dependencias** permite a A llamar a métodos de una abstracción que B implementa, haciendo posible que A llame a B en tiempo de ejecución, pero B depende de una interfaz que controla A durante la compilación (Es decir se invierte la dependencia típica de tiempo de compilación)

En **Tiempo de Ejecución** el programa no cambia, pero introduciendo interfaces permite reemplazar diferentes implementaciones. La práctica de **[[Punto Net Inyección de Dependencias|Punto Net Inyección de Dependencias]]** se hace posible siguiendo el principio de **Inversión de Dependencias**.

![[Pasted image 20250625103905.png]]