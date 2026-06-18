
# Interfaces e Implementaciones

Existe un caso especial para usar codificaciones. Imagine por ejemplo que crea un factoria abstracta ¿Qué nombres debe asignar? ¿IShapeFactory y ShapeFactory?. La I inicial, tan habitual en los archivos de legado actuales es en el mejor de los casos una distracción y en el peor un exceso de información. No quiero que mis usuarios sepan que se trata de una interfaz. Si tengo que codificar la interfaz o la implementación, opto por esta última. Es mejor usar ShapeFactoryImp o CShapeFactory
