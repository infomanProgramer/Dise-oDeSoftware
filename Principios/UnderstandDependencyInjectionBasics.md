## Objetivos

- Registrar servicios y resolverlos usando DI

### Creando el nuevo proyecto

1. Creamos una aplicación de consola
2. Añadimos el paquete Nuget [Microsoft.Extensions.DependencyInjection](https://www.nuget.org/packages/Microsoft.Extensions.DependencyInjection): ![[Pasted image 20250703123806.png]]
3. Las abstracciones para DI en .NET esta definidas en este paquete Nuget
	1. **IServiceCollection:** Define un contrato para una colección de descriptores del servicio
	2. **IServiceProvider:** Define un mecanismo para recuperar un objeto de servicio
	3. **ServiceDescriptor:** Describe un servicio con su tipo de servicio, implementación y ciclo de vida
### Creando servicios

No todos los servicios son creados de la misma forma por ejemplo
- Algunos servicios requieren una nueva instancias cada vez que el contenedor de servicios los obtiene *(transient)*
- Otros son compartidos a través de las solicitudes *(scoped)*
- Para el ciclo entero de la aplicación *(singleton)*

1. Creamos un archivo C# llamado **IConsole.css**

~~~c#
public interface IConsole
{
    void WriteLine(string message);
}
~~~

2. Creamos el archivo **DefaultConsole.cs**

~~~c#
internal sealed class DefaultConsole : IConsole
{
    public bool IsEnabled { get; set; } = true;

    void IConsole.WriteLine(string message)
    {
        if (IsEnabled is false)
        {
            return;
        }

        Console.WriteLine(message);
    }
}
~~~
El código precedente representa la implementación por defecto de la interface **IConsole**. El método **WriteLine** condicionalmente escribe en la consola

3. Creamos el archivo **IGreetingService.cs** con el siguiente código:

~~~c#
public interface IGreetingService
{
    string Greet(string name);
}
~~~

4. Ahora añadimos el archivo **DefaultGreetingService.cs** con el siguiente código:

~~~c#
internal sealed class DefaultGreetingService(IConsole console) : IGreetingService
{
    public string Greet(string name)
    {
        var greeting = $"Hello, {name}!";

        console.WriteLine(greeting);

        return greeting;
    }
}
~~~


El código precedente representa la implementación por defecto de la interface **IGreetingService**. La implementación del servicio requiere **IConsole** como parámetro primario del constructor. El método greet:

- Crea un saludo dado el nombre
- Llama al método WriteLine en la instancia IConsole
- Devuelve el saludo a quien lo llama

El último servicio a crear es el archivo **FarewellService.cs**, añadiendo el siguiente código:

~~~c#
public class FarewellService(IConsole console)
{
    public string SayGoodbye(string name)
    {
        var farewell = $"Goodbye, {name}!";

        console.WriteLine(farewell);

        return farewell;
    }
}
~~~

**FarewellService** representa un tipo concreto, no una interface. Y se deberia declara como público para hacerlo accesible a los consumidores. A diferencia de otros tipos de implementación de servicios declarados como **internal** (solo visibles dentro del mismo [[Ensamblado|ensamblado]]) o **sealed** (no se pueden heredar). Este código demuestra que no todos los servicios necesitan ser interfaces.

Por último se actualiza la clase Program con: 

~~~c#
using Microsoft.Extensions.DependencyInjection;

// 1. Create the service collection.
var services = new ServiceCollection();

// 2. Register (add and configure) the services.
services.AddSingleton<IConsole>(
    implementationFactory: static _ => new DefaultConsole
    {
        IsEnabled = true
    });
services.AddSingleton<IGreetingService, DefaultGreetingService>();
services.AddSingleton<FarewellService>();

// 3. Build the service provider from the service collection.
var serviceProvider = services.BuildServiceProvider();

// 4. Resolve the services that you need.
var greetingService = serviceProvider.GetRequiredService<IGreetingService>();
var farewellService = serviceProvider.GetRequiredService<FarewellService>();

// 5. Use the services
var greeting = greetingService.Greet("David");
var farewell = farewellService.SayGoodbye("David");
~~~

El codigo precedente se realizán los siguientes pasos:

- Se crea una nueva instancia de **ServiceCollection**
- Registra y configura los servicios en el **ServiceCollection**
	- **IConsole** que utiliza la sobrecarga de fabrica de implementación, devuelve un tipo ***DefaultConsole*** con ***IsEnabled*** configurado en ***true*** usa una [[Lambda|lambda]] para configurar el objeto, en este caso activando la propiedad IsEnabled
	- El servicio **IGreetingService** es añadido con una implementación correspondiente del tipo **DefaultGreetingService**
	- El servicio **FarewallService** es añadido como un tipo concreto
- Construimos **ServiceProvider** desde **ServiceCollection**
- Resolvemos los servicios **IGreetingService** y **FarewellServices**

 ![[Pasted image 20250715110543.png]]
 