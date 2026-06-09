# Un breve descripción de lo que se aprendera

- **Parte I: Creación de una arquitectura para admitir el modelo de dominios**
	- **Modelado de dominio:** Problemas comerciales complejos deben reflejarse en código, en forma de un modelo de dominio. Pero por que siempre parece ser tan difícil hacerlo sin enredarse con problemas de infraestructura. En esta capitulo mostramos como comenzar con un modelo de dominio que no tiene dependencias externas y PU. Mas adelante volvemos a los patrones DDD para discutir como elegir el agregado correcto y como esta elección se relaciona con cuestiones de integridad de datos
	- **Patrones repositorio:** Mantener el modelo libre de dependencias. Creamos una capa de abstracción en torno al almacenamiento persistente y creamos una capa de servicio para definir los puntos de entrada a nuestro sistema ya sea una API Flask o una CLI.
	- **Algunas reflexiones sobre pruebas y abstracciones:** Como elegir las abstracciones y cual es su papel en la elección de como se acopla nuestro software. Después de presentar el patrón de capa de servicio, hablamos un poco sobre como lograr una pirámide de prueba y escribir pruebas unitarias en el nivel mas alto posible de abstracción
- **Parte II: Arquitectura impulsada por eventos**
	- **Arquitectura basada en eventos:** Presentamos otros tres patrones que se refuerzan mutuamente, los patrones de: 
		- Eventos de dominio
		- Bus de mensajes
		- Controlador
	- **Segregación de responsabilidad de consulta de comando:** Segregación de responsabilidad de consulta de comando, con y sin eventos
	- **Inyección de dependencias:** Ordenamos nuestras dependencias explicitas e implícitas e implementamos un marco de inyección de dependencias simple
