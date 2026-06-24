# Usar nombres que se puedan buscar

Los nombre de una letra y las constantes numéricas tienen un problema: no son fáciles de encontrar en el texto. Se puede detectar  MAX_CLASSES_PER_STUDENT, pero el número 7 resulta mas complicado. Las búsquedas pueden devolver el digito como parte de nombres de archivo, otras definiciones de constantes o expresiones en las que se use con otra intención.

Del mismo modo, el nombre "e" es una opción pobre para variables que programador tenga que buscar.

En este aspecto, los nombres extensos superan a los breves y cualquier nombre que se pueda buscar supera a una constante en el código

Según el autor es bueno usar nombres de una letra que se puedan usar como variables locales dentro de métodos breves.

**Regla de Oro**

La longitud del nombre debe corresponderse al tamaño de su ámbito N5. Si la variable o constante se usa en varios puntos del código, debe asignarle un nombre que se pueda buscar. Compare:

~~~python
for (int j=0; j<34; j++) \'7b 
	s += (t[j]*4)/5; \'7d 
~~~
con:
~~~python
int realDaysPerIdealDay = 4; 
const int WORK_DAYS_PER_WEEK = 5; 
int sum = 0; 
for (int j = 0; j < NUMBER_OF_TASKS; j++) 
	int realTaskDays = taskEstimate[j] * realDaysPerIdealDay; 
	int realTaskWeeks = (realdays / WORK_DAYS_PER_WEEK); 
	sum += realTaskWeeks;
~~~

En este ejemplo sum no es un nombre especialmente útil, pero al menos se puede buscar. Se usa una función mas extensa, pero comprobara que resulta mas fácil buscar WORK_DAYS_PER_WEEK que todas las instancias de 5 y filtrar las listas a los casos con el significado adecuado.

