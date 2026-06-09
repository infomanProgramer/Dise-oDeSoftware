Hay numerosas rozones para crear servicios de larga duración como: 

- Procesamiento de datos intensivo de CPU
- Poner en cola, elementos de trabajo en segundo plano.
- Realizar una operación basada en tiempo según un cronograma.

Los servicios en segundo plano no tienen una interface de usuario. Anteriormente con **.NET Framework** los desarrolladores podían crear *servicios Windows*. Ahora con **.NET** puedes usar **BackgroundServices** el cual es una implementación de **IHostedServices** o implementar la tuya propia.

.Net no esta restringido a Windows sino que puedes desarrollar servicios en segundo plano multiplataforma

### Terminología

- **Background Service:** El tipo [BackgroundService](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.hosting.backgroundservice)
- **Hosted Service:** Implementación de [IHostedService](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.hosting.ihostedservice), o el [IHostedService](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.hosting.ihostedservice)
- **Long-running Service:** Cualquier servicio que se ejecuta constantemente
- **Windows Service:** La infraestrucutura de un Servicio Windows, ahora disponible en .NET
- **Worker Service:** La plantilla de un Worker Service


