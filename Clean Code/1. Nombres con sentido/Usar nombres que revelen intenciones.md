Elegir nombres correctos lleva tiempo, pero también ahorra trabajo. Por ello, preste atención a los nombres y cámbielos cuando encuentre otros mejores.

El nombre de una variable, función o clase debe responder a una serie de cuestiones básicas. Debe indicar por qué existe, que hace y como se usa. Si un nombre requiere un comentario, significa que no revela su cometido.

~~~c#
int d; //tiempo transcurrido en días
~~~

El nombre d no revela nada. No evoca una sensación de tiempo transcurrido, ni de días. Debe elegir un nombre que especifique lo que se mide y la unidad de dicha medida

~~~c#
int elapsedTimeInDays;
int daysSinceCreation;
int daysSinceModification;
int fileAgeInDays;
~~~

La elección de nombres que revelen intenciones facilita considerablemente la comprensión y la modificación del código

¿Para que sirve el siguiente código?

~~~c#
public List getThem()
	List list1 = new ArrayList();
	for (int[] x : theList)
	if (x[0] == 4)
		list1.add(x); 
	return list1; 
~~~

**¿Por que es complicado saber la función de este código?**

No hay expresiones complejas. Los espacios y el sangrado son razonables. Solo hay tres variables y dos constantes. No tiene clases complejas o métodos polimórficos, solo una lista de matrices

El problema no es la simplicidad del código sino su carácter implícito: el grado en el que el contexto no es explicito en propio código, Implícitamente el código requiere que sepamos las respuestas a las siguientes preguntas:
- ¿Qué contiene theList?
- ¿Qué significado tiene el subíndice cero de un elemento de theList?
- ¿Qué importancia tiene el valor 4?
- ¿Cómo se usa la lista devuelta?

Las respuestas a estas preguntas no se encuentra en el código, pero se podrían haber incluido

~~~c#
public List getFlaggedCells() 
	List flaggedCells = new ArrayList(); 
	for (int[] cell : gameBoard) 
		if (cell[STATUS_VALUE] == FLAGGED) 
			flaggedCells.add(cell); 
	return flaggedCells;
~~~

La simplicidad del código no ha cambiado. Sigue teniendo los mismos operadores y constantes y el mismo número de niveles anidados, pero ahora es muchos mas explicito.

- Podemos crear una sencilla clase para las celdas en lugar de usar una matriz de elementos int.
- Puede incluir una función que revele el objetivo (con el nombre isFlagged) para ocultar los números. El resultado es una nueva versión de la función:

~~~c#
public List getFlaggedCells()
	List flaggedCells = new ArrayList<Cell>(); 
	for (Cell cell : gameBoard)
		if (cell.isFlagged()) 
			flaggedCells.add(ce11); 
	return flaggedCells; 
~~~