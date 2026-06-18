
# Prefijos de miembros

No es necesario añadir m_ como prefijo a los nombres de variables. Las clases y funciones tienen el tamaño necesario para no tener que hacerlo

~~~c#
public class Part 
	private String m_dsc; // La descripción textual 
	void setName(String name) 
		m_dsc = name;

public class Part
	String description; 
	void setDescription(String description)
		this.description = description;
~~~
Además los usuarios aprenden rápidamente a ignorar el prefijo o sufijo y fijarse en la parte con sentido de nombre. Los prefijo son un indicio de código antiguo