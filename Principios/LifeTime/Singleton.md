En los ciclos de vida Singleton los servicios se crean:
- La primera vez que ellos son solicitados
- Por el desarrollador, cuando provee la instancia de implementación directamente en el contenedor. Este enfoque rara vez es necesario

Cada solicitud posterior a la implementación del servicio, desde el contenedor de inyección de dependencias se usara la misma instancia