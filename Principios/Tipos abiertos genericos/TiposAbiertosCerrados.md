## Tipo Abierto

Es aquel que tiene parámetros específicos sin especificar 

~~~c#
List<T> //en este ejemplo no se sabe que tipo de datos es T
Dictionary<TKey, TValues> //no se ha especificado ni Tkey ni TValue
T[] //Un arreglo es genérico si su tipo también lo es, donde T es genérico 
~~~
## Tipo Cerrado

Es cuando todos los parámetros genéricos están definidos con tipos reales

~~~c#
List<string> //cerrado
Dictionary<int, string> //cerrado
List<List<int>> //cerrado
~~~

**¿Cuándo se usan?**

- En tiempo de compilación se puede trabajar con datos abiertos por que todavía se esta planificando
- En tiempo de ejecución todo debe estar cerrado, ya que no se puede ejecutar sobre algo que no se sabe lo que es