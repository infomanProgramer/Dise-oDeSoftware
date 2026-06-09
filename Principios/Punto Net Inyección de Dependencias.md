También ver [[RolesOfDependencyInjection|roles de la Inyección de dependencias]]

Una dependencia es un un objeto que depende de otro objeto. Veamos el siguiente ejemplo:

- La clase MeesageWriter tiene el método Write

~~~c#
public class MessageWriter
{
    public void Write(string message)
    {
        Console.WriteLine($"MessageWriter.Write(message: \"{message}\")");
    }
}
~~~
Una clase puede hacer crear una instancia de la clase **MessageWriter** y usar el método **Write**
~~~c#
public class Worker : BackgroundService
{
    private readonly MessageWriter _messageWriter = new();

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _messageWriter.Write($"Worker running at: {DateTimeOffset.Now}");
            await Task.Delay(1_000, stoppingToken);
        }
    }
}
~~~
La clase crea y depende directamente de la clase **MessageWriter** lo que hace que haya un fuerte acoplamiento entre ambas clases. Este tipo de acoplamiento deberia evitarse por las siguientes razones:

- Para reemplazar **MessageWriter** con una implementación diferente, la clase **Worker** se debe modificar
- Si MessageWriter tiene dependencias. tambien se debe configurar en la clase Worker
- En esta implementación es dificil hacer pruebas unitarias

La inyección de dependencias aborda estos problemas a través de:

- El uso de una interface o clase base para abstraer la implementación de dependencias
- Registro de una dependencia en un contenedor de servicio .Net incorpora un contenedor de servicio **IServiceProvider**. Los servicios o dependencias se deben registrar al inicio de la aplicación. Ese registro se hace en una colección llamada **IServiceCollection** (lista de servicios que la aplicación necesita). Una vez que todos los servicios son añadidos, usa **BuilderServiceProvider** para crear el contenedor en el Servicio
- La ***Inyección*** del servicio dentro el constructor de la clase donde es usado. El framework toma la responsabilidad de crear la instancia de la dependencia y deshacerse de el cuando ya no es necesario

**Ejemplo**

La interfaz **IMessageWriter** define el método **Write**

~~~c#
namespace DependencyInjection.Example;

public interface IMessageWriter
{
    void Write(string message);
}
~~~

La interface es implementada por un tipo concreto **MessageWriter**:

~~~c#
namespace DependencyInjection.Example;

public class MessageWriter : IMessageWriter
{
    public void Write(string message)
    {
        Console.WriteLine($"MessageWriter.Write(message: \"{message}\")");
    }
}
~~~

El código de ejemplo registra el servicio **IMessageWriter** con un tipo concreto **MessageWriter**. El método **AddSingleton** registra el servicio con un siclo de vida ([[LifeTime]]) *singleton*

~~~c#
using DependencyInjection.Example;

HostApplicationBuilder builder = Host.CreateApplicationBuilder(args);

builder.Services.AddHostedService<Worker>();
builder.Services.AddSingleton<IMessageWriter, MessageWriter>();

using IHost host = builder.Build();

host.Run();
~~~
En el código precedente

![[Pasted image 20250701101830.png]]

- Se crea una instancia de host app builder
- Configurar los servicios registrand
	- El Worker esta como un servicio alojado. Ver [[WorkerServices|WorkerServices]]
	- La interface **IMessageWriter** como un servicio Singleton con una implementación correspondiente de la clase **MessageWriter**

El anfitrión contiene al proveedor del servicio de inyección de dependencias. También contiene todos los servicios requeridos para automáticamente instanciar el Worker y proveer la implementación de IMessageWriter como argumento

~~~c#
namespace DependencyInjection.Example;

public sealed class Worker(IMessageWriter messageWriter) : BackgroundService
{
    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            messageWriter.Write($"Worker running at: {DateTimeOffset.Now}");
            await Task.Delay(1_000, stoppingToken);
        }
    }
}
~~~

Usando el patrón de diseño DI, el worker service:
- No usa el tipo concreto MessageWriter, solo la interface IMessageWriter que lo implementa. Eso hace facil cambiar la implementación que el worker service usa sin modificar el worker service
- No se crea una instancia de MessageWriter. La instancia es creada por el contenedor DI

La implementación de IMessageWriter puede ser mejorada usando un registro de API incorporado

~~~c#
namespace DependencyInjection.Example;

public class LoggingMessageWriter(
    ILogger<LoggingMessageWriter> logger) : IMessageWriter
{
    public void Write(string message) =>
        logger.LogInformation("Info: {Msg}", message);
}
~~~
El nuevo método de AddSingleton registra la implementación de IMessageWriter
~~~c#
builder.Services.AddSingleton<IMessageWriter, LoggingMessageWriter>();
~~~

El tipo **HostApplicationBuilder** (builder) es parte del paquete Nuget ***Microsoft.Extensions.Hosting***
- **LoggingMessageWriter** depende de ILogger\<TCategoryName\>, el cual se solicita en el constructor
- ILogger \<TCategoryName\> es un framework-provided service

El contenedor resuelve ILogger\<TCategoryName\> tomando las ventajas de los [[TiposAbiertosCerrados|tipos genéricos]] abiertos eliminando la necesidad de registrar ***cada tipo construido genérico***

No es inusual usar la inyección de dependencias de forma encadenada, lo que quiere decir que una dependencia solicitada a su vez necesita de otras dependencias lo que forma un árbol de dependencias




**Resumen grafico de la Inyección de Dependencias**

![[Pasted image 20250627115227.png]]


