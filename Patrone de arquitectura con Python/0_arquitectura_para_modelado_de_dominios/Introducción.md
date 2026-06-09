# Introducción

### Descripción general

Los desarrolladores a menudos dependen de los modelos de datos y carecen de comprensión de los modelos de dominio, lo que lleva a una lógica de negocio dispersa y a centrarse en el esquema de la base de datos en lugar de la funcionalidad del sistema.

### Objetivos

Esta sección hace hincapié en la creación de un modelo de objetos sólido mediante el Desarrollo Dirigido por Pruebas (TDD) y en el mantenimiento de su independencia de los detalles técnicos, promoviendo un código que no dependa de la persistencia y API estables para la refactorización.

### Patrones de diseño clave Presentados

- **Patrón Repositorio:** Abstracción del almacenamiento persistente.
- **Patrón Capa de Servicio:** Definición de los límites de los casos de uso.
- **Patrón Unidad de Trabajo:** Facilita las operaciones atómicas.
- **Patrón Agregado:** Garantiza la integridad de los datos.

### ¿Por qué nuestros diseños salen mal?

- Los sistemas de software tienden al caos.
- Los sistemas de software caóticos se caracterizan por una similitud de funciones: Controladores de API que tienen conocimiento del dominio y envían correos y realizan registros.
- Clases de negocios que no realizan cálculos pero realizan operaciones de E/S y todo acoplado a todo lo demás.

Una gran bola de barro es el estado natural del software de la misma manera que la naturaleza salvaje es el estado natural de su jardín, Se necesita energía y dirección para evitar el colapso.





