Los métodos deben tener nombres de verbo como:

- postPayment, 
- deletePage  
- save.

Los métodos de acceso, de modificación y los predicados deben tener como nombre su valor y usar como prefijo *get*, *set* e *is* de acuerdo al estandar de **javabean**

~~~c#
string name = employee.getName();
customer.setName(“mike”);
if (paycheck.isPosted()){}
~~~

Al sobrecargar constructores, use métodos de factoría estáticos con nombres que describan los argumentos. Por ejemplo:

~~~c#
Complex fulcrumPoint = Complex.FromRealNumber(23.0); //Complejo de un número real
//es mejor que:
Complex fulcrumPoint = new Complex(23.0);
~~~

Refuerce su uso convirtiendo en privados sus constructores correspondientes
