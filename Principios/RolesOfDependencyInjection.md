
En la inyección de dependencias, Las dependencias de una clase son inyectadas desde fuera, en ese sentido la clase crea o gestiona sus dependencias internamente. Esto patrón tiene cuatro roles:

![[Pasted image 20250627115911.png]]

- **Cliente:** Es el componente o clase que depende de los servicios que proporciona otra clase o modulo. El cliente recibe las dependencias desde el *Inyector*
- **Servicio:** Es el componente o clase que proporciona una funcionalidad en particular y esta hecho para ser independiente de los clientes
- **Inyector:** El servicio debe ser inyectado dentro del *Cliente* por el Inyector
- **Interface:** Define el contrato o conjunto de métodos que el servicio debe implementar