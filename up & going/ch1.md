# You Don't Know JS: Up & Going
# Chapter 1: Into Programming

## Contenido

* Código
   * Statements
   * Expresiones
   * Ejecutando un programa
* Inténtalo tú mismo
   * Output
   * Input
* Operators
* Valores y tipos
   * Conversión Entre Types
* Code Comments
* Variables
* Blocks
* Conditionals
* Loops
* Functions
   * Scope
* Practice
* Review

Bienvenido a la serie *You Don't Know JS* (*YDKJS*).

*Up & Going* es una introducción a varios conceptos básicos de programación, por supuesto, nos inclinamos hacia JavaScript (a menudo abreviado JS) específicamente, y sobre cómo abordar y entender el resto de los títulos de esta serie. Especialmente si recién te estás iniciando en la programación y/o JavaScript, este libro explorará brevemente lo que necesitas para *ponerlo en marcha*.

Este libro comienza explicando los principios básicos de la programación a un nivel muy alto. Es principalmente la intención si está comenzando *YDKJS* con poca o ninguna experiencia previa en programación, y está buscando estos libros para ayudarlo a comenzar un camino hacia la comprensión de la programación a través de la lente de JavaScript.

El Capítulo 1 debe abordarse como una visión general rápida de las cosas sobre las que querrá aprender más y practicar para *introducirse en la programación*. También hay muchos otros recursos fantásticos de introducción a la programación que pueden ayudarte a profundizar en estos temas, y te animo a que aprendas de ellos además de este capítulo.

Una vez que se sienta cómodo con los conceptos básicos de programación general, el Capítulo 2 lo ayudará a familiarizarse con la programación de JavaScript. El Capítulo 2 presenta de qué se trata JavaScript, pero, de nuevo, no es una guía completa. ¡Para eso es el resto de los libros * YDKJS *!

Si ya te sientes bastante cómodo con JavaScript, primero revisa el Capítulo 3 como un breve vistazo de lo que puedes esperar de *YDKJS*, ¡luego salta a la derecha!

## Código

Vamos a empezar desde el principio.

Un programa, a menudo referido como *código fuente* o simplemente *código*, es un conjunto de instrucciones especiales para decirle a la computadora qué tareas debe realizar. Por lo general, el código se guarda en un archivo de texto, aunque con JavaScript también puede escribir el código directamente en una consola de desarrollador en un navegador, que veremos en breve.

Las reglas para el formato válido y las combinaciones de instrucciones se denominan *lenguaje informático*, a veces se denomina *sintaxis*, de manera muy similar a como el inglés le dice cómo deletrear palabras y cómo crear oraciones válidas usando palabras y puntuación.

### Statements

En un lenguaje de computadora, un grupo de palabras, números y operadores que realizan una tarea específica es una *statements*. En JavaScript, una declaración puede verse como sigue:

```js
a = b * 2;
```

Los caracteres `a` y` b` se denominan *variables* (consulte "Variables"), que son como cajas simples en los que puede almacenar cualquiera de sus cosas. En los programas, las variables contienen valores (como el número `42`) para Ser utilizado por el programa. Piense en ellos como marcadores simbólicos de los valores en sí mismos.

En contraste, el `2` es solo un valor en sí mismo, llamado *valor literal*, porque está solo, sin ser almacenado en una variable.

Los caracteres `=` y `*` son *operadores* (consulte "Operadores"): realizan acciones con los valores y variables, como la asignación y la multiplicación matemática.

La mayoría de las declaraciones en JavaScript concluyen con un punto y coma (`;`) al final.

La declaración `a = b * 2;` le dice a la computadora, aproximadamente, que obtenga el valor actual almacenado en la variable `b`, multiplique ese valor por `2`, luego almacene el resultado en otra variable que llamamos `a` .

Los programas son solo colecciones de muchas de estas dsentencias, que en conjunto describen todos los pasos necesarios para llevar a cabo el propósito de su programa.

### Expresiones

Las sentencias se componen de una o más *expresiones*. Una expresión es cualquier referencia a una variable o valor, o un conjunto de variables y valores combinados con operadores.

Por ejemplo:

```js
a = b * 2;
```

Esta sentencia tiene cuatro expresiones en ella:

* `2` is a *expresión de valor literal*
* `b` is a *variable expression*, lo que significa recuperar su valor actual
* `b * 2` es una *expresión aritmética*, que significa hacer la multiplicación
* `a = b * 2` es una *expresión de asignación*, que significa asignar el resultado de la expresión `b * 2` a la variable` a` (más adelante las asignaciones)

Una expresión general que está sola también se denomina *sentencia de expresión*, como la siguiente:

```js
b * 2;
```

Este tipo de sentencia de expresión no es muy común ni útil, ya que generalmente no tendría ningún efecto en la ejecución del programa; recuperaría el valor de `b` y lo multiplicaría por `2`, pero luego no se hace nada con ese resultado.

Una expression statement más común es una *call expression* (consulte "Funciones"), ya que toda la declaración es la expresión de llamada de función en sí misma:

```js
alert( a );
```

### Ejecutando un programa

¿Cómo esas colecciones de sentencia de programación le dicen a la computadora qué hacer? El programa necesita ser *ejecutado*, también conocido como *correr el programa*.

Sentencias como `a = b * 2` son útiles para los desarrolladores al leer y escribir, pero en realidad no están en una forma que la computadora pueda entender directamente. Por lo tanto, se utiliza una utilidad especial en la computadora (ya sea un *intérprete* o un *compilador*) para traducir el código que usted escribe en comandos que una computadora puede entender.

Para algunos lenguajes de computadora, esta traducción de comandos se realiza generalmente de arriba a abajo, línea por línea, cada vez que se ejecuta el programa, lo que generalmente se llama *interpretar* el código.

Para otros idiomas, la traducción se realiza antes de tiempo, llamada *compilar* el código, de modo que cuando el programa *se ejecuta* más tarde, lo que se está ejecutando es en realidad las instrucciones de la computadora ya compiladas listas para usar.

Por lo general, se afirma que JavaScript se *interpreta*, porque su código fuente de JavaScript se procesa cada vez que se ejecuta. Pero eso no es del todo exacto. El motor de JavaScript en realidad *compila* el programa sobre la marcha y luego ejecuta inmediatamente el código compilado.

**Nota:** Para obtener más información sobre la compilación de JavaScript, consulte los dos primeros capítulos de *Scope & Closures* t
ítulo de esta serie.

## Inténtalo tú mismo

Este capítulo presentará cada concepto de programación con simples fragmentos de código, todos escritos en JavaScript (¡obviamente!).

No se puede enfatizar lo suficiente: mientras repasa este capítulo, y es posible que deba dedicar tiempo a repasarlo varias veces, debe practicar cada uno de estos conceptos escribiendo el código usted mismo. La forma más sencilla de hacerlo es abrir la consola de herramientas para desarrolladores en el navegador más cercano (Firefox, Chrome, IE, etc.).

**Sugerencia:** Normalmente, puede iniciar la consola del desarrollador con un método abreviado de teclado o desde un elemento del menú. Para obtener información más detallada sobre el inicio y el uso de la consola en su navegador favorito, consulte "Mastering The Developer Tools Console" (http://blog.teamtreehouse.com/mastering-developer-tools-console). Para escribir varias líneas en la consola a la vez, use `<shift> + <enter>` para pasar a la siguiente línea. Una vez que haya pulsado `<enter>` por sí mismo, la consola ejecutará todo lo que acaba de escribir.

Familiarizémonos con el proceso de ejecución de código en la consola. En primer lugar, sugiero abrir una pestaña vacía en su navegador. Prefiero hacer esto escribiendo `about:blank` en la barra de direcciones. Luego, asegúrese de que su consola de desarrollador esté abierta, como acabamos de mencionar.

Ahora, escriba este código y vea cómo se ejecuta: 

```js
a = 21;

b = a * 2;

console.log( b );
```

Escribir el código anterior en la consola en Chrome debería producir algo como lo siguiente:

<img src="fig1.png" width="500">

Vamos, inténtalo. ¡La mejor manera de aprender programación es comenzar a codificar!

### Output

En el fragmento de código anterior, usamos `console.log (..)`. Brevemente, veamos de qué se trata esa línea de código.

Es posible que haya adivinado, pero así es como imprimimos el texto (también conocido como *output* para el usuario) en la consola del desarrollador. Hay dos características de esa declaración que debemos explicar.

Primero, se hace referencia a la parte `log (b)` como una llamada de función (consulte "Funciones"). Lo que está sucediendo es que estamos entregando la variable `b` a esa función, que le pide que tome el valor de `b` y lo imprima en la consola.

En segundo lugar, la parte `console` es una referencia de objeto donde se encuentra la función `log (..)`. Cubrimos los objetos y sus propiedades con más detalle en el Capítulo 2.

Otra forma de crear resultados que puede ver es ejecutar una instrucción `alert (..)`. Por ejemplo:

```js
alert( b );
```

Si lo ejecuta, notará que, en lugar de imprimir la salida en la consola, muestra un cuadro emergente "OK" con el contenido de la variable `b`. Sin embargo, el uso de `console.log (..)` hará que aprender a codificar y ejecutar sus programas en la consola sea más fácil que usar `alert (..)`, porque puede generar muchos valores a la vez sin interrumpir el navegador interfaz.

Para este libro, usaremos `console.log (..)` para la salida.

### Input

Mientras discutimos el resultado, también puede preguntarse sobre *input* (es decir, recibir información del usuario).

La forma más común que ocurre es que la página HTML muestre elementos de formulario (como cuadros de texto) a un usuario en el que puedan escribir, y luego usar JS para leer esos valores en las variables de su programa.

Pero hay una manera más fácil de obtener información con fines de aprendizaje y demostración simples, como lo que hará a lo largo de este libro. Use la función `prompt (..)`

```js
age = prompt( "Please tell me your age:" );

console.log( age );
```

Como puede haber adivinado, el mensaje que pasa a `prompt (..)` - en este caso, `"Please tell me your age:"` - está impreso en la ventana emergente.

Esto debería verse similar a lo siguiente:

<img src="fig2.png" width="500">

Una vez que envíe el texto de entrada haciendo clic en "OK", observará que el valor que ingresó se almacena en la variable `age`, que luego *output* con `console.log(..)`:

<img src="fig3.png" width="500">

Para mantener las cosas simples mientras aprendemos los conceptos básicos de programación, los ejemplos en este libro no requerirán input. Pero ahora que has visto cómo usar `prompt (..)`, si quieres desafiarte a ti mismo, puedes intentar usar input en tus exploraciones de los ejemplos.

## Operators

Los operadores son como realizamos acciones sobre variables y valores. Ya hemos visto dos operadores de JavaScript, el `=` y el `*`.

El operador `*` realiza la multiplicación matemática. Bastante simple, ¿verdad?

El operador `=` se usa para la *asignación*: primero calculamos el valor en el *lado derecho* (source value) del `=` y luego lo colocamos en la variable que especificamos en el *lado izquierdo* (target variable).

**Advertencia:** Esto puede parecer un extraño un orden inverso para especificar la asignación. En lugar de `a = 42`, es posible que algunos prefieran cambiar el orden para que el valor de origen esté a la izquierda y la variable de destino a la derecha, como `42 -> a` (¡esto no es válido en JavaScript!). Desafortunadamente, la forma ordenada `a = 42`, y variaciones similares, son bastante frecuente en los lenguajes de programación modernos. Si se siente antinatural, dedique un poco de tiempo a ensayar ese pedido mentalmente para acostumbrarse a él.

Considerar:

```js
a = 2;
b = a + 1;
```

Aquí, asignamos el valor `2` a la variable `a`. Luego, obtenemos el valor de la variable `a` (aún` 2`), le agregamos `1` que resulta en el valor `3`, luego almacenamos ese valor en la variable `b`.

Si bien no es técnicamente un operador, necesitará la palabra clave `var` en cada programa, ya que es la forma principal en que *declara* (aka *create*) *var*iables (consulte" Variables ").

Siempre debe declarar la variable por su nombre antes de usarla. Pero solo necesita declarar una variable una vez para cada *scope alcance* (consulte Scope""); Puede usarse tantas veces después de eso como sea necesario. Por ejemplo:

```js
var a = 20;

a = a + 1;
a = a * 2;

console.log( a );	// 42
```

Estos son algunos de los operadores más comunes en JavaScript:

* Asignación: `=` como en `a = 2`.
* Matemáticos: `+` (suma), `-` (resta), `*` (multiplicación), y `/` (división), como en `a * 3`.
* Asignación compuesta: `+=`, `-=`, `*=` y `/=` son operadores compuestos que combinan una operación matemática con asignación, como en `a += 2` (igual que `a = a + 2`).
* Incremento/Decremento: `++` (incremento), `--` (decremento), como en `a++` (similar a `a = a + 1`).
* Acceso a la propiedad del objeto: `.` como en` console.log()`.
   Los objetos son valores que contienen otros valores en ubicaciones con nombre específicOs llamadas propiedades. `obj.a` significa un objeto llamado `obj` con una propiedad de nombre `a`. Alternativamente, se puede acceder a las propiedades como `obj["a"]`. Vea el capítulo 2.
* Igualdad: `==` (loose-equals), `===` (strict-equals), `!=` (loose not-equals), `!==` (strict not-equals), como en `a == b`.
   Consulte "Values & Types" en el Capítulo 2.   
* Comparación: `<` (less than), `>` (greater than), `<=` (less than or loose-equals), `>=` (greater than or loose-equals), como en `a <= b`.
   Consulte "Values & Types" en el Capítulo 2.
* Lógicos: `&&` (and), `||` (or), como en `a || b` que selecciona ya sea `a` *o* `b`.
   Estos operadores se utilizan para expresar condicionales compuestos (ver "Conditionals"), cuando `a` *o*` b` es verdadero.
   
**Nota:** Para más detalles, y cobertura de operadores no mencionados aquí, vea the Mozilla Developer Network (MDN)'s "Expressions and Operators" (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators).

## Valores y tipos

Si le pregunta a un empleado en una tienda de teléfonos cuánto cuesta un determinado teléfono y dice "noventa y nueve, noventa y nueve" (es decir, $99.99), le están dando una cifra numérica real en dólares que representa lo que necesita pagar (mas impuestos) para comprarlo. Si desea comprar dos de esos teléfonos, puede hacer fácilmente el cálculo mental para duplicar ese valor y obtener $199.98 por su costo.

Si ese mismo empleado toma otro teléfono similar pero dice que es "gratis", no le están dando un número, sino otro tipo de representación de su costo esperado ($0.00): la palabra "gratis" . "

Cuando más tarde pregunte si el teléfono incluye un cargador, esa respuesta podría haber sido "sí" o "no".

De manera muy similar, cuando expresas valores en un programa, eliges diferentes representaciones para esos valores en función de lo que planeas hacer con ellos.

Estas diferentes representaciones de valores se denominan *types* en la terminología de programación. JavaScript tiene tipos incorporados para cada uno de estos valores denominados *primitive*:

* Cuando necesitas hacer matemáticas, quieres un `number`.
* Cuando necesita imprimir un valor en la pantalla, necesita un `string` (uno o más caracteres, palabras, oraciones).
* Cuando necesitas tomar una decisión en tu programa, necesitas un `boolean` (`true` o `false`).

Los valores que se incluyen directamente en el código fuente se denominan *literals*. Los literales `string` están rodeados por comillas dobles `"..."` o comillas simples (`'...'`) - la única diferencia es la preferencia estilística. Los literales `number` y `boolean` se presentan como están (es decir, `42`,`true`, etc.).

Considerar:

```js
"I am a string";
'I am also a string';

42;

true;
false;
```

Más allá de los tipos de valores `string`/`number`/`boolean`, es común que los lenguajes de programación proporcionen *arrays*, *objects*, *functions* y más. Cubriremos mucho más sobre valores y tipos a lo largo de este capítulo y el siguiente.

### Conversión Entre Types

Si tiene un `number` pero necesita imprimirlo en la pantalla, debe convertir el valor en un `string`, y en JavaScript esta conversión se llama "coercion". De manera similar, si alguien ingresa una serie de caracteres numéricos en un formulario en una página de comercio electrónico, eso es un `string`, pero si necesita usar ese valor para realizar operaciones matemáticas, debe "forzarlo (coerce)" a un "número" .

JavaScript proporciona varias facilidades diferentes para conversión entre *types*. Por ejemplo:

```js
var a = "42";
var b = Number( a );

console.log( a );	// "42"
console.log( b );	// 42
```

Use `Number(..)` (una función incorporada) como se muestra en una  *explicit* coercion de cualquier otro tipo al tipo `number`. Eso debería ser bastante sencillo.

Pero un tema controvertido es qué sucede cuando intentas comparar dos valores que no son del mismo tipo, lo que requeriría una *implicit* coercion.

Al comparar la cadena `"99.99"` con el número `99.99`, la mayoría de la gente estaría de acuerdo en que son equivalentes. Pero no son exactamente iguales, ¿verdad? Es el mismo valor en dos representaciones diferentes, dos tipos *diferentes*. Se podría decir que son "ligeramente iguales", ¿verdad?

Para ayudarlo en estas situaciones comunes, a veces JavaScript activará *implicitly* coerce para convertir los valores a los tipos correspondientes.

Entonces, si usa el operador `==` suelto es igual para hacer la comparación `"99.99"== 99.99`, JavaScript convertirá el lado izquierdo` "99.99" `a su `number` equivalente a `99.99`. La comparación se convierte entonces en '99.99 == 99.99', que por supuesto es `true`.

Si bien está diseñado para ayudarlo, implicit coercion puede crear confusión si no se ha tomado el tiempo de aprender las reglas que gobiernan su comportamiento. La mayoría de los desarrolladores de JS nunca lo han hecho, por lo que el sentimiento común es que la coacción implícita es confusa y perjudica a los programas con errores inesperados, por lo que debe evitarse. Incluso a veces se le conoce como una falla en el diseño del lenguaje.

Sin embargo, la implicit coercion es un mecanismo que *puede aprenderse* y además *debe ser aprendido* por cualquier persona que desee tomar en serio la programación de JavaScript. ¡No solo no es confuso una vez que aprenda las reglas, sino que también puede mejorar sus programas! El esfuerzo merece la pena.

**Nota:** Para obtener más información sobre la coercion, consulte el Capítulo 2 de este título y el Capítulo 4 de los *Types & Grammar* de esta serie.

## Code Comments

El empleado de la tienda de teléfonos podría anotar algunas notas sobre las características de un teléfono recientemente lanzado o sobre los nuevos planes que ofrece su compañía. Estas notas son solo para el empleado, no para que las lean los clientes. Sin embargo, estas notas ayudan a la empleada a hacer mejor su trabajo al documentar cómo y qué debería decir a los clientes.

Una de las lecciones más importantes que puede aprender acerca de cómo escribir código es que no es solo para la computadora. El código es tanto, si no más, tanto para el desarrollador como para el compilador.

Su computadora solo se preocupa por el código de máquina, una serie de 0 y 1 binarios que proviene de *compilación*. Hay una cantidad casi infinita de programas que podrías escribir que producen la misma serie de 0 y 1. Las decisiones que tome sobre cómo escribir su programa son importantes, no solo para usted, sino también para los demás miembros de su equipo e incluso para su futuro.

Debe esforzarse no solo por escribir programas que funcionen correctamente, sino programas que tengan sentido cuando se examinen. Puede hacer un gran esfuerzo en ese esfuerzo al elegir buenos nombres para sus variables (ver "Variables") y funciones (ver "Functions").

Pero otra parte importante son los comentarios en código. Estos son fragmentos de texto en su programa que se insertan únicamente para explicar las cosas a un humano. El intérprete/compilador siempre ignorará estos comentarios.

Hay muchas opiniones sobre lo que hace un código bien comentado; Realmente no podemos definir reglas universales absolutas. Pero algunas observaciones y pautas son bastante útiles:

* Código sin comentarios es subóptimo.
* Demasiados comentarios (uno por línea, por ejemplo) es probablemente un signo de código mal escrito.
* Los comentarios deben explicar *por qué*, no *qué*. Opcionalmente, pueden explicar *cómo* si eso es particularmente confuso.

En JavaScript, hay dos tipos de comentarios posibles: un comentario de una sola línea y un comentario de varias líneas.

Considerar:

```js
// This is a single-line comment

/* But this is
       a multiline
             comment.
                      */
```

El comentario de una sola línea `//` es apropiado si va a colocar un comentario justo encima de una sola declaración, o incluso al final de una línea. Todo lo que está en la línea después de `//` se trata como un comentario (y, por lo tanto, el compilador lo ignora), hasta el final de la línea. No hay restricción a lo que puede aparecer dentro de un comentario de una sola línea.

Considerar:

```js
var a = 42;		// 42 is the meaning of life
```

El comentario multilínea `/ * .. * /` es apropiado si tiene varias líneas para explicar en su comentario.

Aquí un uso común de comentarios multilínea:

```js
/* The following value is used because
   it has been shown that it answers
   every question in the universe. */
var a = 42;
```

También puede aparecer en cualquier lugar de una línea, incluso en el centro de una línea, porque el `* /` lo termina. Por ejemplo:


```js
var a = /* arbitrary value */ 42;

console.log( a );	// 42
```

Lo único que no puede aparecer dentro de un comentario multilínea es un `*/`, porque eso se interpretaría para terminar el comentario.

Definitivamente, deseará comenzar su aprendizaje de la programación comenzando con el hábito de comentar el código. A lo largo del resto de este capítulo, verás que uso comentarios para explicar cosas, así que haz lo mismo en tu propia práctica. Confía en mí, todos los que lean tu código te lo agradecerán.

## Variables

Most useful programs need to track a value as it changes over the course of the program, undergoing different operations as called for by your program's intended tasks.

The easiest way to go about that in your program is to assign a value to a symbolic container, called a *variable* -- so called because the value in this container can *vary* over time as needed.

In some programming languages, you declare a variable (container) to hold a specific type of value, such as `number` or `string`. *Static typing*, otherwise known as *type enforcement*, is typically cited as a benefit for program correctness by preventing unintended value conversions.

Other languages emphasize types for values instead of variables. *Weak typing*, otherwise known as *dynamic typing*, allows a variable to hold any type of value at any time. It's typically cited as a benefit for program flexibility by allowing a single variable to represent a value no matter what type form that value may take at any given moment in the program's logic flow.

JavaScript uses the latter approach, *dynamic typing*, meaning variables can hold values of any *type* without any *type* enforcement.

As mentioned earlier, we declare a variable using the `var` statement -- notice there's no other *type* information in the declaration. Consider this simple program:

```js
var amount = 99.99;

amount = amount * 2;

console.log( amount );		// 199.98

// convert `amount` to a string, and
// add "$" on the beginning
amount = "$" + String( amount );

console.log( amount );		// "$199.98"
```

The `amount` variable starts out holding the number `99.99`, and then holds the `number` result of `amount * 2`, which is `199.98`.

The first `console.log(..)` command has to *implicitly* coerce that `number` value to a `string` to print it out.

Then the statement `amount = "$" + String(amount)` *explicitly* coerces the `199.98` value to a `string` and adds a `"$"` character to the beginning. At this point, `amount` now holds the `string` value `"$199.98"`, so the second `console.log(..)` statement doesn't need to do any coercion to print it out.

JavaScript developers will note the flexibility of using the `amount` variable for each of the `99.99`, `199.98`, and the `"$199.98"` values. Static-typing enthusiasts would prefer a separate variable like `amountStr` to hold the final `"$199.98"` representation of the value, because it's a different type.

Either way, you'll note that `amount` holds a running value that changes over the course of the program, illustrating the primary purpose of variables: managing program *state*.

In other words, *state* is tracking the changes to values as your program runs.

Another common usage of variables is for centralizing value setting. This is more typically called *constants*, when you declare a variable with a value and intend for that value to *not change* throughout the program.

You declare these *constants*, often at the top of a program, so that it's convenient for you to have one place to go to alter a value if you need to. By convention, JavaScript variables as constants are usually capitalized, with underscores `_` between multiple words.

Here's a silly example:

```js
var TAX_RATE = 0.08;	// 8% sales tax

var amount = 99.99;

amount = amount * 2;

amount = amount + (amount * TAX_RATE);

console.log( amount );				// 215.9784
console.log( amount.toFixed( 2 ) );	// "215.98"
```

**Note:** Similar to how `console.log(..)` is a function `log(..)` accessed as an object property on the `console` value, `toFixed(..)` here is a function that can be accessed on `number` values. JavaScript `number`s aren't automatically formatted for dollars -- the engine doesn't know what your intent is and there's no type for currency. `toFixed(..)` lets us specify how many decimal places we'd like the `number` rounded to, and it produces the `string` as necessary.

The `TAX_RATE` variable is only *constant* by convention -- there's nothing special in this program that prevents it from being changed. But if the city raises the sales tax rate to 9%, we can still easily update our program by setting the `TAX_RATE` assigned value to `0.09` in one place, instead of finding many occurrences of the value `0.08` strewn throughout the program and updating all of them.

The newest version of JavaScript at the time of this writing (commonly called "ES6") includes a new way to declare *constants*, by using `const` instead of `var`:

```js
// as of ES6:
const TAX_RATE = 0.08;

var amount = 99.99;

// ..
```

Constants are useful just like variables with unchanged values, except that constants also prevent accidentally changing value somewhere else after the initial setting. If you tried to assign any different value to `TAX_RATE` after that first declaration, your program would reject the change (and in strict mode, fail with an error -- see "Strict Mode" in Chapter 2).

By the way, that kind of "protection" against mistakes is similar to the static-typing type enforcement, so you can see why static types in other languages can be attractive!

**Note:** For more information about how different values in variables can be used in your programs, see the *Types & Grammar* title of this series.

## Blocks

The phone store employee must go through a series of steps to complete the checkout as you buy your new phone.

Similarly, in code we often need to group a series of statements together, which we often call a *block*. In JavaScript, a block is defined by wrapping one or more statements inside a curly-brace pair `{ .. }`. Consider:

```js
var amount = 99.99;

// a general block
{
	amount = amount * 2;
	console.log( amount );	// 199.98
}
```

This kind of standalone `{ .. }` general block is valid, but isn't as commonly seen in JS programs. Typically, blocks are attached to some other control statement, such as an `if` statement (see "Conditionals") or a loop (see "Loops"). For example:

```js
var amount = 99.99;

// is amount big enough?
if (amount > 10) {			// <-- block attached to `if`
	amount = amount * 2;
	console.log( amount );	// 199.98
}
```

We'll explain `if` statements in the next section, but as you can see, the `{ .. }` block with its two statements is attached to `if (amount > 10)`; the statements inside the block will only be processed if the conditional passes.

**Note:** Unlike most other statements like `console.log(amount);`, a block statement does not need a semicolon (`;`) to conclude it.

## Conditionals

"Do you want to add on the extra screen protectors to your purchase, for $9.99?" The helpful phone store employee has asked you to make a decision. And you may need to first consult the current *state* of your wallet or bank account to answer that question. But obviously, this is just a simple "yes or no" question.

There are quite a few ways we can express *conditionals* (aka decisions) in our programs.

The most common one is the `if` statement. Essentially, you're saying, "*If* this condition is true, do the following...". For example:

```js
var bank_balance = 302.13;
var amount = 99.99;

if (amount < bank_balance) {
	console.log( "I want to buy this phone!" );
}
```

The `if` statement requires an expression in between the parentheses `( )` that can be treated as either `true` or `false`. In this program, we provided the expression `amount < bank_balance`, which indeed will either evaluate to `true` or `false` depending on the amount in the `bank_balance` variable.

You can even provide an alternative if the condition isn't true, called an `else` clause. Consider:

```js
const ACCESSORY_PRICE = 9.99;

var bank_balance = 302.13;
var amount = 99.99;

amount = amount * 2;

// can we afford the extra purchase?
if ( amount < bank_balance ) {
	console.log( "I'll take the accessory!" );
	amount = amount + ACCESSORY_PRICE;
}
// otherwise:
else {
	console.log( "No, thanks." );
}
```

Here, if `amount < bank_balance` is `true`, we'll print out `"I'll take the accessory!"` and add the `9.99` to our `amount` variable. Otherwise, the `else` clause says we'll just politely respond with `"No, thanks."` and leave `amount` unchanged.

As we discussed in "Values & Types" earlier, values that aren't already of an expected type are often coerced to that type. The `if` statement expects a `boolean`, but if you pass it something that's not already `boolean`, coercion will occur.

JavaScript defines a list of specific values that are considered "falsy" because when coerced to a `boolean`, they become `false` -- these include values like `0` and `""`. Any other value not on the "falsy" list is automatically "truthy" -- when coerced to a `boolean` they become `true`. Truthy values include things like `99.99` and `"free"`. See "Truthy & Falsy" in Chapter 2 for more information.

*Conditionals* exist in other forms besides the `if`. For example, the `switch` statement can be used as a shorthand for a series of `if..else` statements (see Chapter 2). Loops (see "Loops") use a *conditional* to determine if the loop should keep going or stop.

**Note:** For deeper information about the coercions that can occur implicitly in the test expressions of *conditionals*, see Chapter 4 of the *Types & Grammar* title of this series.

## Loops

During busy times, there's a waiting list for customers who need to speak to the phone store employee. While there's still people on that list, she just needs to keep serving the next customer.

Repeating a set of actions until a certain condition fails -- in other words, repeating only while the condition holds -- is the job of programming loops; loops can take different forms, but they all satisfy this basic behavior.

A loop includes the test condition as well as a block (typically as `{ .. }`). Each time the loop block executes, that's called an *iteration*.

For example, the `while` loop and the `do..while` loop forms illustrate the concept of repeating a block of statements until a condition no longer evaluates to `true`:

```js
while (numOfCustomers > 0) {
	console.log( "How may I help you?" );

	// help the customer...

	numOfCustomers = numOfCustomers - 1;
}

// versus:

do {
	console.log( "How may I help you?" );

	// help the customer...

	numOfCustomers = numOfCustomers - 1;
} while (numOfCustomers > 0);
```

The only practical difference between these loops is whether the conditional is tested before the first iteration (`while`) or after the first iteration (`do..while`).

In either form, if the conditional tests as `false`, the next iteration will not run. That means if the condition is initially `false`, a `while` loop will never run, but a `do..while` loop will run just the first time.

Sometimes you are looping for the intended purpose of counting a certain set of numbers, like from `0` to `9` (ten numbers). You can do that by setting a loop iteration variable like `i` at value `0` and incrementing it by `1` each iteration.

**Warning:** For a variety of historical reasons, programming languages almost always count things in a zero-based fashion, meaning starting with `0` instead of `1`. If you're not familiar with that mode of thinking, it can be quite confusing at first. Take some time to practice counting starting with `0` to become more comfortable with it!

The conditional is tested on each iteration, much as if there is an implied `if` statement inside the loop.

We can use JavaScript's `break` statement to stop a loop. Also, we can observe that it's awfully easy to create a loop that would otherwise run forever without a `break`ing mechanism.

Let's illustrate:

```js
var i = 0;

// a `while..true` loop would run forever, right?
while (true) {
	// stop the loop?
	if ((i <= 9) === false) {
		break;
	}

	console.log( i );
	i = i + 1;
}
// 0 1 2 3 4 5 6 7 8 9
```

**Warning:** This is not necessarily a practical form you'd want to use for your loops. It's presented here for illustration purposes only.

While a `while` (or `do..while`) can accomplish the task manually, there's another syntactic form called a `for` loop for just that purpose:

```js
for (var i = 0; i <= 9; i = i + 1) {
	console.log( i );
}
// 0 1 2 3 4 5 6 7 8 9
```

As you can see, in both cases the conditional `i <= 9` is `true` for the first 10 iterations (`i` of values `0` through `9`) of either loop form, but becomes `false` once `i` is value `10`.

The `for` loop has three clauses: the initialization clause (`var i=0`), the conditional test clause (`i <= 9`), and the update clause (`i = i + 1`). So if you're going to do counting with your loop iterations, `for` is a more compact and often easier form to understand and write.

There are other specialized loop forms that are intended to iterate over specific values, such as the properties of an object (see Chapter 2) where the implied conditional test is just whether all the properties have been processed. The "loop until a condition fails" concept holds no matter what the form of the loop.

## Functions

The phone store employee probably doesn't carry around a calculator to figure out the taxes and final purchase amount. That's a task she needs to define once and reuse over and over again. Odds are, the company has a checkout register (computer, tablet, etc.) with those "functions" built in.

Similarly, your program will almost certainly want to break up the code's tasks into reusable pieces, instead of repeatedly repeating yourself repetitiously (pun intended!). The way to do this is to define a `function`.

A function is generally a named section of code that can be "called" by name, and the code inside it will be run each time. Consider:

```js
function printAmount() {
	console.log( amount.toFixed( 2 ) );
}

var amount = 99.99;

printAmount(); // "99.99"

amount = amount * 2;

printAmount(); // "199.98"
```

Functions can optionally take arguments (aka parameters) -- values you pass in. And they can also optionally return a value back.

```js
function printAmount(amt) {
	console.log( amt.toFixed( 2 ) );
}

function formatAmount() {
	return "$" + amount.toFixed( 2 );
}

var amount = 99.99;

printAmount( amount * 2 );		// "199.98"

amount = formatAmount();
console.log( amount );			// "$99.99"
```

The function `printAmount(..)` takes a parameter that we call `amt`. The function `formatAmount()` returns a value. Of course, you can also combine those two techniques in the same function.

Functions are often used for code that you plan to call multiple times, but they can also be useful just to organize related bits of code into named collections, even if you only plan to call them once.

Consider:

```js
const TAX_RATE = 0.08;

function calculateFinalPurchaseAmount(amt) {
	// calculate the new amount with the tax
	amt = amt + (amt * TAX_RATE);

	// return the new amount
	return amt;
}

var amount = 99.99;

amount = calculateFinalPurchaseAmount( amount );

console.log( amount.toFixed( 2 ) );		// "107.99"
```

Although `calculateFinalPurchaseAmount(..)` is only called once, organizing its behavior into a separate named function makes the code that uses its logic (the `amount = calculateFinal...` statement) cleaner. If the function had more statements in it, the benefits would be even more pronounced.

### Scope

If you ask the phone store employee for a phone model that her store doesn't carry, she will not be able to sell you the phone you want. She only has access to the phones in her store's inventory. You'll have to try another store to see if you can find the phone you're looking for.

Programming has a term for this concept: *scope* (technically called *lexical scope*). In JavaScript, each function gets its own scope. Scope is basically a collection of variables as well as the rules for how those variables are accessed by name. Only code inside that function can access that function's *scoped* variables.

A variable name has to be unique within the same scope -- there can't be two different `a` variables sitting right next to each other. But the same variable name `a` could appear in different scopes.

```js
function one() {
	// this `a` only belongs to the `one()` function
	var a = 1;
	console.log( a );
}

function two() {
	// this `a` only belongs to the `two()` function
	var a = 2;
	console.log( a );
}

one();		// 1
two();		// 2
```

Also, a scope can be nested inside another scope, just like if a clown at a birthday party blows up one balloon inside another balloon. If one scope is nested inside another, code inside the innermost scope can access variables from either scope.

Consider:

```js
function outer() {
	var a = 1;

	function inner() {
		var b = 2;

		// we can access both `a` and `b` here
		console.log( a + b );	// 3
	}

	inner();

	// we can only access `a` here
	console.log( a );			// 1
}

outer();
```

Lexical scope rules say that code in one scope can access variables of either that scope or any scope outside of it.

So, code inside the `inner()` function has access to both variables `a` and `b`, but code in `outer()` has access only to `a` -- it cannot access `b` because that variable is only inside `inner()`.

Recall this code snippet from earlier:

```js
const TAX_RATE = 0.08;

function calculateFinalPurchaseAmount(amt) {
	// calculate the new amount with the tax
	amt = amt + (amt * TAX_RATE);

	// return the new amount
	return amt;
}
```

The `TAX_RATE` constant (variable) is accessible from inside the `calculateFinalPurchaseAmount(..)` function, even though we didn't pass it in, because of lexical scope.

**Note:** For more information about lexical scope, see the first three chapters of the *Scope & Closures* title of this series.

## Practice

There is absolutely no substitute for practice in learning programming. No amount of articulate writing on my part is alone going to make you a programmer.

With that in mind, let's try practicing some of the concepts we learned here in this chapter. I'll give the "requirements," and you try it first. Then consult the code listing below to see how I approached it.

* Write a program to calculate the total price of your phone purchase. You will keep purchasing phones (hint: loop!) until you run out of money in your bank account. You'll also buy accessories for each phone as long as your purchase amount is below your mental spending threshold.
* After you've calculated your purchase amount, add in the tax, then print out the calculated purchase amount, properly formatted.
* Finally, check the amount against your bank account balance to see if you can afford it or not.
* You should set up some constants for the "tax rate," "phone price," "accessory price," and "spending threshold," as well as a variable for your "bank account balance.""
* You should define functions for calculating the tax and for formatting the price with a "$" and rounding to two decimal places.
* **Bonus Challenge:** Try to incorporate input into this program, perhaps with the `prompt(..)` covered in "Input" earlier. You may prompt the user for their bank account balance, for example. Have fun and be creative!

OK, go ahead. Try it. Don't peek at my code listing until you've given it a shot yourself!

**Note:** Because this is a JavaScript book, I'm obviously going to solve the practice exercise in JavaScript. But you can do it in another language for now if you feel more comfortable.

Here's my JavaScript solution for this exercise:

```js
const SPENDING_THRESHOLD = 200;
const TAX_RATE = 0.08;
const PHONE_PRICE = 99.99;
const ACCESSORY_PRICE = 9.99;

var bank_balance = 303.91;
var amount = 0;

function calculateTax(amount) {
	return amount * TAX_RATE;
}

function formatAmount(amount) {
	return "$" + amount.toFixed( 2 );
}

// keep buying phones while you still have money
while (amount < bank_balance) {
	// buy a new phone!
	amount = amount + PHONE_PRICE;

	// can we afford the accessory?
	if (amount < SPENDING_THRESHOLD) {
		amount = amount + ACCESSORY_PRICE;
	}
}

// don't forget to pay the government, too
amount = amount + calculateTax( amount );

console.log(
	"Your purchase: " + formatAmount( amount )
);
// Your purchase: $334.76

// can you actually afford this purchase?
if (amount > bank_balance) {
	console.log(
		"You can't afford this purchase. :("
	);
}
// You can't afford this purchase. :(
```

**Note:** The simplest way to run this JavaScript program is to type it into the developer console of your nearest browser.

How did you do? It wouldn't hurt to try it again now that you've seen my code. And play around with changing some of the constants to see how the program runs with different values.

## Review

Learning programming doesn't have to be a complex and overwhelming process. There are just a few basic concepts you need to wrap your head around.

These act like building blocks. To build a tall tower, you start first by putting block on top of block on top of block. The same goes with programming. Here are some of the essential programming building blocks:

* You need *operators* to perform actions on values.
* You need values and *types* to perform different kinds of actions like math on `number`s or output with `string`s.
* You need *variables* to store data (aka *state*) during your program's execution.
* You need *conditionals* like `if` statements to make decisions.
* You need *loops* to repeat tasks until a condition stops being true.
* You need *functions* to organize your code into logical and reusable chunks.

Code comments are one effective way to write more readable code, which makes your program easier to understand, maintain, and fix later if there are problems.

Finally, don't neglect the power of practice. The best way to learn how to write code is to write code.

I'm excited you're well on your way to learning how to code, now! Keep it up. Don't forget to check out other beginner programming resources (books, blogs, online training, etc.). This chapter and this book are a great start, but they're just a brief introduction.

The next chapter will review many of the concepts from this chapter, but from a more JavaScript-specific perspective, which will highlight most of the major topics that are addressed in deeper detail throughout the rest of the series.
