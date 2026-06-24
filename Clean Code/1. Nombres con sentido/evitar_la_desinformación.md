# Evitar la desinformación

Los programadores deben evitar dejar *pistas falsas que dificulten el significado del código*. Debemos evitar palabras cuyo significado se aleje de lo que pretendemos. Por ejemplo:

~~~c#
hp //hipotenusa
aix
sco
~~~

son nombre de *variables pobres*. Aunque se trate del código de una hipotenusa y hp parezca la abreviatura correcta, puede no serlo

El lector tendría que adivinar mejor seria:

~~~c#
hipotenusa = calcularHipotenusa(a, b)
~~~

### No llames "List" a algo que no es una lista

No haga referencia a un grupo de cuentas como **accountList** a menos que realmente sea una lista. Si contenedor de cuentas no es realmente una lista puede provocar falsas conclusiones. Por lo tanto resulta mas adecuado usar **accountGroup**, **bunchOfAccounts** o simplemente **accounts**

**Ejemplo peligroso**

~~~c#
accountList = getAccounts();
~~~

Pero internamente es:

~~~c#
accountList = {
	"123": Account(),
	"456": Account()
}
~~~

Eso es un diccionario / mapa no una lista

Mejores nombres serian:
- accounts
- accountGroup
- accountsById
- accountMap

### Variaciones mínimas (errores visuales)

Evite usar nombre con variaciones mínimas ¿Cuánto tiempo se tarda en apreciar la sutil diferencia entre:

~~~c#
XYZControllerForEfficientHandlingOfStrings //y 
XYZControllerForEfficientHandlingOfString? 
~~~

Visualmente son idénticas

**Problema**

- Son difíciles de distinguir rápidamente
- Generan errores al importar
- Confunden en revisiones de código
- Aumentan el tiempo cognitivo

**¿Cuál es el principio profundo aquí?**
El código se lee mucho más de lo que se escribe.

Si un nombre:

- Sugiere una estructura incorrecta
- Tiene múltiples significados
- Es ambiguo
- Se parece demasiado a otro
- Usa abreviaturas innecesarias
- Entonces estás agregando carga cognitiva innecesaria.

Y eso genera:

- Bugs
- Malentendidos
- Código frágil
- Tiempo perdido

**Regla mental práctica**

Antes de nombrar algo pregúntate:

- ¿El nombre describe exactamente lo que es?
- ¿Podría interpretarse de otra forma?
- ¿Refleja correctamente el tipo de dato?
- ¿Es fácil de diferenciar de otros nombres?
- ¿Alguien nuevo en el proyecto lo entendería?
- Si la respuesta es sí a todas → buen nombre.