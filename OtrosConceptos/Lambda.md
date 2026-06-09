Es una forma abreviada de escribir una función anónima (una función sin nombre).
Se utiliza comúnmente para pasar un ***comportamiento como argumento*** a otros métodos:

Sintaxis básica

~~~
(parámetros) => expresión o bloque
~~~

**Lambda con múltiples parámetros**

~~~c#
Func<int, int, int> sumar = (a, b) => a+b
~~~

**Lambda con bloque de código**

~~~c#
Action<string> saludar = nombre => {
	Console.WriteLine("Hola "+nombre);
}

saludar("Rafael") //Imprime "Hola Rafael"
~~~

**Lambda para verificar si un numero es par**

~~~c#
Func<int, bool> esPar = x => x%2 == 0;

Console.WriteLine(esPar(6)) //Resultado True
Console.WriteLine(esPar(7)) //Resultado False
~~~

**Lambda con bloque de código**

~~~c#
Func<int, string> evaluarNumero = x => {
	if(x>0) return "Positivo";
	if(x<0) return "Negativo";
}

Console.WriteLine(evaluarNumero(4)) //Resultado "Positivo"
Console.WriteLine(evaluarNumero(-1)) //Resultado "Negativo"
~~~

## Casos de Uso

**Listar los número pares**

~~~c#
var numeros = new List<int> { 1, 2, 3, 4, 5, 6 };

var pares = numeros.Where(n => n % 2 == 0); // Lambda anónima usada directamente
~~~

donde **n => n%2 == 0** es una lambda pasada directamente al **Where()**

**Convertir una lista de nombres a mayúsculas**

~~~c#
var nombres = new List<string> { "rafael", "juan", "ana" };
var enMayuscula = nombres.Select(n => n.ToUpper());

foreach (var nombre in enMayuscula)
    Console.WriteLine(nombre);

~~~

## Función anónima sin parámetros

