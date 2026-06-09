Di es gestionado añadiendo servicios y configurandolos en un **IServiceCollection**. La interface **IHost** expone la instancia **IServiceProvider**, la cual actua como un contenedor de todos los servicios registrados

**Objetivos** 

- Crear una aplicación de consola .NET que usa la inyección de dependencias
- Construir y configurar un Host Genérico
- Escribe varias interfaces y las implementaciones correspondientes
- Usar la vida útil del servicio y el alcance para DI

**Instalamos el paquete Nuget:**

![[Pasted image 20250717115257.png]]

### Añadimos la interfaces

En este ejemplo aprenderemos a manejar la vida útil del servicio. Crearemos varias interfaces que representan diferentes tiempo de vida de servicios

![[Pasted image 20250717152135.png]]

Todas las subinterfaces de IReportServiceLifetime implementan explicitamente IReportServiceLifetime.Lifetime por defecto

### Añadimos implementaciones por defecto

No es necesario que las implementaciones seán **internal** o **sealed**. Pero es común tratar las implementaciones como **internal** para evitar fugas de tipos de implementación al consumidor externo. Ademas desde que cada tipo no es extendido, es marcado como **sealed**



