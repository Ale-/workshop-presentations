% CodeUp (III) : Patrones de diseño
% [Ale](414c45.net)
% Hangar, 21 de Mayo 2015

# Patrones de diseño

El concepto de patrón de diseño surge en el entorno de la programación orientada a objetos y proviene de la arquitectura, de las teorías de Christopher Alexander. Los patrones de diseño vienen a ser estrategias de programación pensadas a funcionar a distintas escalas, de lo micro a lo macro. Los primeros en sistematizarlos fueron el conocido como 'Gang of Four' (Gamma, Helm, Johnson y Vissides).

# Básicamente

La función de los patrones es múltiple:
* Hacer el código más reusable y mantenible.
* Crear componentes para una abstracción del lenguaje. Esto facilita la comunicación entre programadores, puede hacer el código comprensible con mayor rapidez y permite la re-apropiación del código con facilidad.
* DRY ('no te repitas a ti mismo'). Dotar de soluciones contrastadas a problemas habituales. 

# Tipos de patrones de diseño

Los patrones de diseño originales se agrupan en tres categorías:

* Patrones de creación
Son estrategias de creación e instanciación de objetos.

* Patrones estructurales
Son patrones que permiten la estructuración del código y los objetos.

* Patrones de comportamiento
Son patrones que tienen que ver con las funcionalidades de los objetos.

Por oposición a los patrones existe también el concepto de anti-patrón. 

# Pero no sólo...

Realmente los patrones de diseño no han parado de crecer y hay multitud de ellos. Lo más importante no es sabérselos todos sino interiorizar sus mecanismos. Para mí los dos más importantes son los siguientes: 
* Favorece la abstracción frente la concreción. La indirección de la abstracción permite que el código no esté confinado a las intenciones del diseño original y permite la ampliación flexible del código a medida que sea necesario.
* Desacopla los funcionamientos y estructuras de las cosas. Favorece la modularidad.

## Un ejemplo

Así, vamos a comenzar con un patrón de diseño que no es de los originales, [interfaz de constantes](https://en.wikipedia.org/wiki/Constant_interface). Las interfaces en OOP son clases abstractas puras que delegan en las clases que las implementan el concretar el comportamiento. Las interfaces sólo pueden estar compuestas por métodos abstractos y campos estáticos finales. El patrón en cuestión viene a ser encapsular en una interfaz todas las constantes de una librería o programa. [Código fuente de PConstants](https://github.com/processing/processing/blob/master/core/src/processing/core/PConstants.java). Las clases que quieran usar dichas constantes sólo tendran que implementar dicha interfaz. Este sería un patrón estructural, porque define una manera de ordenar nuestro código.

## ¡Claro!

En este ejemplo tan sencillo vemos las virtudes y mecanismos habituales de un patrón de diseño. Se desacoplan los datos del comportamiento y se usan la indirección y la abstracción. El resultado final es una estructuración más limpia y fácil de mantener...

## Pero... ¿seguro?

También traigo este ejemplo a colación porque hay discusión en torno a el, habiendo opiniones que lo consideran un anti-patrón de diseño, con pocos beneficios respecto a sus desventajas. La alternativa sería crear una clase final normal con un constructor privado que se importa estáticamente. Es decir, ¡tampoco hay que fetichizar la indirección ni la abstracción!

```java
final class Constants {
	private Constants() { // restrict instantiation }
	static final double PI = 3.14;
}

import static Constants.PI;
 
public class Calculations {
	void printPi() { println(PI); }
}

```

# Los patrones de comportamiento

Los patrones de comportamiento distribuyen responsabilidades/comportamientos/funcionalidades entre objetos y asignan patrones de comunicación entre objetos.

## _Command_

Es de los más fáciles de entender y empezar a aplicar, siendo de gran utilidad. El patrón _Command_ encapsula un método en un objeto. Esta es la manera de resolver _callbacks_ en OOP, es decir es la respuesta a la clásica pregunta: ¿cómo le paso un método a otro? También es la manera en que se crea la funcionalidad de _deshacer_ (Ctrl+Z), ya que los objetos los podemos almacenar a diferencia de los métodos.

## _Iterator_

El patrón _Iterador_ está pensado para poder recorrer un conjunto de objetos de una manera predeterminada. En la mayoría de lenguajes de programación, los elementos iterables disponen de la instrucción _for each_, que permite de una manera limpia efectuar operaciones sobre un conjunto en la manera deseada por el programador. Java viene ya 'equipado' con un par de clases al efecto, [_Iterable_](https://docs.oracle.com/javase/7/docs/api/java/lang/Iterable.html) e [_Iterator_](https://docs.oracle.com/javase/7/docs/api/java/util/Iterator.html). Los objetos _Iterables_ contienen un _Iterador_, que es el que resuelve el recorrido sobre los elementos. Los objetos _Iterables_ soportan la instrucción _for each_ de Java.

## _Visitor_

El patrón _Visitador_ desacopla el comportamiento de un objeto de su definición, de manera que el comportamiento lo efectua una clase externa, que lo 'visita'. Esto permite extender de manera limpia la funcionalidad de un objeto a discreción sin necesidad de modificar su código.

# Patrones estructurales

## _Decorator_

## _Facade_

# Los patrones de creación

Los patrones de creación son bastante habituales. Estos patrones delegan la creación de objetos en otros objetos. Es decir, en vez de crear objetos con el operador _new()_, usamos métodos definidos en otros objetos (volvemos a la indirección).  

## _Generator_

## _Factory_

## _Singleton_

Un patrón Singleton impide que una clase se instancie más de una vez en un programa. Para ello hace al constructor de la clase privado, sólo accesible desde un método público que comprueba si ya se ha producido una instanciación de la clase e impidiendo en este caso la generación de un nuevo objeto.

