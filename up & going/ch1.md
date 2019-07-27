# You Don't Know JS: Up & Going
# Chapter 1: Into Programming

## Contenido

* Código
   * Sentencias
   * Expresiones
   * Ejecutando un programa
* Inténtalo tú mismo
   * Output
   * Input
* Operadores
* Valores y tipos
   * Conversión Entre Types
* Comentarios
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

### Sentencias

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

## Operadores

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

## Comentarios

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

La mayoría de los programas útiles deben rastrear un valor a medida que cambia a lo largo del programa, sometiéndose a diferentes operaciones según lo requieran las tareas previstas de su programa.

La forma más fácil de hacerlo en su programa es asignar un valor a un contenedor simbólico, llamado *variable*, llamado así porque el valor en este contenedor puede *variar* con el tiempo según sea necesario.

En algunos lenguajes de programación, declara una variable (contenedor) para mantener un tipo específico de valor, como `number` o `string`. *Static typing*, también conocida como *type enforcement*, se cita normalmente como un beneficio para la corrección del programa al evitar conversiones de valores no deseadas.

Otros lenguajes enfatizan tipos para valores en vez de variables. *Weak typing*, también conocida como *dynamic typing*, permite que una variable retenga cualquier tipo de valor en cualquier momento. Por lo general, se cita como un beneficio para la flexibilidad del programa al permitir que una sola variable represente un valor, independientemente del tipo de forma que ese valor pueda tomar en cualquier momento dado en el flujo lógico del programa.

JavaScript utiliza este último enfoque, *dynamic typing*, lo que significa que las variables pueden contener valores de cualquier *tipo* sin ningún  *type* enforcement.

Como se mencionó anteriormente, declaramos una variable usando la declaración `var` - note que no hay otra información de *type* en la declaración. Considere este programa simple:

```js
var amount = 99.99;

amount = amount * 2;

console.log( amount );		// 199.98

// convert `amount` to a string, and
// add "$" on the beginning
amount = "$" + String( amount );

console.log( amount );		// "$199.98"
```

La variable `amount` comienza manteniendo el número `99.99`, y luego contiene el resultado de `number` de `amount * 2`, que es `199.98`.

El primer comando `console.log (..)` tiene que *implícitamente* forzar ese valor `number` a un `string` para imprimirlo.

Luego, la declaración `amount = "$" + String(amount)` *explícitamente* obliga al valor `199.98` convertirse en un `string` y agrega un carácter `"$"` al principio. En este punto, `amount` ahora contiene el valor `string` `"$199.98"`, por lo que la segunda instrucción `console.log (..)` no necesita hacer ninguna coercion para imprimirlo.

Los desarrolladores de JavaScript notarán la flexibilidad de usar la variable `amount` para cada uno de los valores `99.99`, `199.98` y `"$199.98"`. Los entusiastas de la escritura estática preferirían una variable separada como `amountStr` para mantener la representación final del valor de `"$199.98"`, porque es un tipo diferente.

De cualquier manera, notará que `amount` tiene un valor que cambia a lo largo del programa, ilustrando el propósito principal de las variables: administrar el *state* del programa.

En otras palabras, *state* está rastreando los cambios en los valores mientras se ejecuta su programa.

Otro uso común de las variables es para centralizar la configuración de valores. Esto se suele llamar *constants*, cuando se declara una variable con un valor y se pretende que ese valor *no cambie* en todo el programa.

Usted declara estas *constants*, a menudo en la parte superior de un programa, por lo que es conveniente que tenga un lugar donde ir para modificar un valor si lo necesita. Por convención, las variables de JavaScript como constantes usualmente están en mayúsculas, con guiones bajos entre varias palabras.

Aquí hay un ejemplo tonto:

```js
var TAX_RATE = 0.08;	// 8% sales tax

var amount = 99.99;

amount = amount * 2;

amount = amount + (amount * TAX_RATE);

console.log( amount );				// 215.9784
console.log( amount.toFixed( 2 ) );	// "215.98"
```

**Nota:** Similar a cómo `console.log (..)` es una función `log(..)` a la que se accede como una propiedad de objeto en el valor de `console`, `toFixed(..)` es una función que puede acceder a los valores de `número`. Los "números" de JavaScript no se formatean automáticamente en dólares: el motor no sabe cuál es su intención y no existe un tipo de moneda. `toFixed(..)` nos permite especificar cuántos decimales nos gustaría redondear a `number`, y produce la `cadena` según sea necesario.

La variable `TAX_RATE` es solo *constante* por convención - no hay nada especial en este programa que impida que se cambie. Pero si la ciudad eleva la tasa del impuesto a las ventas al 9%, aún podemos actualizar nuestro programa fácilmente al establecer el valor asignado `TAX_RATE` en `0.09` en un solo lugar, en lugar de encontrar muchas apariciones del valor `0.08` esparcidas en todo el Programa y actualización de todos ellos.

La versión más reciente de JavaScript en el momento de escribir esto (comúnmente llamada "ES6") incluye una nueva forma de declarar *constants*, usando `const` en lugar de `var`:

```js
// as of ES6:
const TAX_RATE = 0.08;

var amount = 99.99;

// ..
```

Las constantes son útiles al igual que las variables con valores sin cambios, excepto que las constantes también impiden cambiar accidentalmente el valor en otro lugar después de la configuración inicial. Si intentó asignar un valor diferente a `TAX_RATE` después de esa primera declaración, su programa rechazará el cambio (y en modo estricto, fallará con un error, consulte "Strict Mode" en el Capítulo 2).

Por cierto, ese tipo de "protección" contra los errores es similar a la aplicación del tipo de tipificación estática, por lo que puede ver por qué los tipos estáticos en otros idiomas pueden ser atractivos.

**Nota:** Para obtener más información sobre cómo se pueden usar diferentes valores en variables en sus programas, consulte el título *Types & Grammar* de esta serie.

## Bloques

El empleado de la tienda de teléfonos debe seguir una serie de pasos para completar la compra a medida que compra su nuevo teléfono.

De manera similar, en el código a menudo necesitamos agrupar una serie de sentencias, lo que a menudo llamamos un *block*. En JavaScript, un bloque se define envolviendo una o más declaraciones dentro de un par de llaves `{ .. }`. Considerar:

```js
var amount = 99.99;

// a general block
{
	amount = amount * 2;
	console.log( amount );	// 199.98
}
```

Este tipo de bloque general `{ .. }` independiente es válido, pero no es tan comúnmente visto en los programas JS. Normalmente, los bloques se adjuntan a alguna otra instrucción de control, como una instrucción `if` (consulte "Conditionals") o un bucle (consulte "Loops"). Por ejemplo:

```js
var amount = 99.99;

// is amount big enough?
if (amount > 10) {			// <-- block attached to `if`
	amount = amount * 2;
	console.log( amount );	// 199.98
}
```

Explicaremos las declaraciones `if` en la siguiente sección, pero como puede ver, el bloque `{ .. }` con sus dos declaraciones se adjunta a `if (amount > 10)`; Las declaraciones dentro del bloque solo se procesarán si el condicional pasa.

**Nota:** A diferencia de la mayoría de las otras declaraciones como `console.log(amount);`, una declaración de bloque no necesita un punto y coma (`;`) para concluirla.

## Condicionales

"¿Desea agregar protectores de pantalla adicionales a su compra, por $9.99?" El amable empleado de la tienda telefónica le ha pedido que tome una decisión. Y es posible que deba consultar primero el *state* actual de su billetera o cuenta bancaria para responder a esa pregunta. Pero obviamente, esto es solo una simple pregunta de "sí o no".

Hay bastantes formas en que podemos expresar *conditionals* (también conocidas como decisiones) en nuestros programas.

El más común es la instrucción `if`. Esencialmente, estás diciendo: "*Si* esta condición es verdadera, haz lo siguiente ...". Por ejemplo:

```js
var bank_balance = 302.13;
var amount = 99.99;

if (amount < bank_balance) {
	console.log( "I want to buy this phone!" );
}
```

La declaración `if` requiere una expresión entre los paréntesis `() `que se puede tratar como `true` o `false`. En este programa, proporcionamos la expresión `amount <bank_balance`, que de hecho evaluará a `true` o `false` dependiendo de la cantidad en la variable `bank_balance`.

Incluso puede proporcionar una alternativa si la condición no es verdadera, denominada cláusula `else`. Considerar:

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

Aquí, si `amount <bank_balance` es `true`, imprimiremos `"I'll take the accessory!"` Y agregaremos el `9.99` a nuestra variable `amount`. De lo contrario, la cláusula `else` dice que solo responderemos cortésmente con `"No, thanks."` y dejaremos `amount` sin cambios.

Como hemos comentado en "Values & Types" anteriormente, los valores que aún no son del tipo esperado a menudo son obligados a ese tipo. La instrucción `if` espera un `boolean`, pero si le pasas algo que aún no es `boolean`, se producirá la coacción.

JavaScript define una lista de valores específicos que se consideran "falsos" porque cuando se les convierte a `boolean`, se convierten en `false`, estos incluyen valores como `0` y `""`. Cualquier otro valor que no esté en la lista de "falsos" es automáticamente "verdadero": cuando se transforman a un "booleano" se convierten en "verdaderos". Los valores de verdad incluyen cosas como `99.99` y `"free"`. Consulte "Truthy & Falsy" en el Capítulo 2 para obtener más información.

*Conditionals* existen en otras formas además del `if`. Por ejemplo, la instrucción `switch` se puede usar como una forma abreviada de una serie de instrucciones `if..else` (ver Capítulo 2). Los bucles (consulte "Bucles") usan un *condicional* para determinar si el bucle debe continuar o detenerse.

**Nota:** Para obtener información más detallada sobre las coerciones que pueden ocurrir implícitamente en las expresiones de prueba de *conditionals*, consulte el Capítulo 4 del título *Types & Grammar* de esta serie.

## Loops

Durante las horas punta, hay una lista de espera para los clientes que necesitan hablar con el empleado de la tienda telefónica. Si bien todavía hay personas en esa lista, solo necesita seguir sirviendo al próximo cliente.

Repetir un conjunto de acciones hasta que falla una determinada condición, en otras palabras, repetir solo mientras la condición se mantiene, es el trabajo de programar los bucles; Los bucles pueden tomar diferentes formas, pero todos satisfacen este comportamiento básico.

Un bucle incluye la condición de prueba así como un bloque (normalmente como `{ .. }`). Cada vez que se ejecuta el bloque de bucle, se denomina *iteration*.

Por ejemplo, el bucle `while` y las formas de bucle `do..while` ilustran el concepto de repetir un bloque de declaraciones hasta que una condición ya no se evalúa como `true`:

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

La única diferencia práctica entre estos bucles es si el condicional se prueba antes de la primera iteración (`while`) o después de la primera iteración (`do..while`).

En cualquiera de las formas, si las pruebas condicionales son falsas, la siguiente iteración no se ejecutará. Eso significa que si la condición inicialmente es "falsa", un bucle `while` nunca se ejecutará, pero un bucle `do..while` se ejecutará solo la primera vez.

A veces, realiza un bucle con el propósito previsto de contar un determinado conjunto de números, como de `0` a` 9` (diez números). Puede hacerlo configurando una variable de iteración de bucle como `i` en el valor `0` e incrementándola en `1` en cada iteración.

**Advertencia:** Por razones históricas, los lenguajes de programación casi siempre cuentan las cosas de forma cero, es decir, comienzan con `0` en lugar de `1`. Si no está familiarizado con ese modo de pensar, puede ser bastante confuso al principio. ¡Tómese un tiempo para practicar el conteo comenzando con `0` para sentirse más cómodo con él!

El condicional se prueba en cada iteración, como si hubiera una declaración implícita `if` dentro del bucle.

Podemos usar la declaración `break` de JavaScript para detener un bucle. Además, podemos observar que es muy fácil crear un bucle que, de lo contrario, se ejecutaría para siempre sin un mecanismo de "interrupción".

Vamos a ilustrar:

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

**Advertencia:** Esta no es necesariamente una forma práctica que querría usar para sus bucles. Se presenta aquí con fines ilustrativos únicamente.

Mientras que un `while` (o `do..while`) puede realizar la tarea manualmente, hay otra forma sintáctica llamada bucle `for` para ese propósito:

```js
for (var i = 0; i <= 9; i = i + 1) {
	console.log( i );
}
// 0 1 2 3 4 5 6 7 8 9
```

Como puede ver, en ambos casos la condicional `i <= 9` es `true` para las primeras 10 iteraciones (`i` de valores` 0` a `9`) de cualquiera de las formas de bucle, pero se convierte en `false` una vez `i` es el valor `10`.

El bucle `for` tiene tres cláusulas: la cláusula de inicialización (`var i = 0`), la cláusula de prueba condicional (`i <= 9`) y la cláusula de actualización (`i = i + 1`). Por lo tanto, si va a contar con sus iteraciones de bucle, `for` es una forma más compacta y, a menudo, más fácil de entender y escribir.

Existen otras formas especializadas de bucle que pretenden iterar sobre valores específicos, como las propiedades de un objeto (ver Capítulo 2) donde la prueba condicional implícita es solo si todas las propiedades se han procesado. El concepto de "bucle hasta que una condición falla" se mantiene independientemente de la forma del bucle.

## Funciones

El empleado de la tienda de teléfonos probablemente no lleva una calculadora para calcular los impuestos y el monto de la compra final. Esa es una tarea que necesita definir una vez y reutilizar una y otra vez. Las probabilidades son que la compañía tenga un registro de pago (computadora, tableta, etc.) con esas "funciones" integradas.

De manera similar, su programa casi seguramente querrá dividir las tareas del código en partes reutilizables, en lugar de repetirse repetidamente (¡intencionalmente!). La forma de hacerlo es definir una `función`.

Una función es generalmente una sección de código con nombre que se puede "llamar" por su nombre, y el código que se encuentra dentro se ejecutará cada vez. Considerar:

```js
function printAmount() {
	console.log( amount.toFixed( 2 ) );
}

var amount = 99.99;

printAmount(); // "99.99"

amount = amount * 2;

printAmount(); // "199.98"
```

Las funciones pueden tomar argumentos (también conocidos como parámetros), valores que usted pasa. Y también pueden devolver un valor opcionalmente.

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
La función `printAmount(..)` toma un parámetro que llamamos `amt`. La función `formatAmount ()` devuelve un valor. Por supuesto, también puede combinar esas dos técnicas en la misma función.

Las funciones a menudo se usan para el código que planea llamar varias veces, pero también pueden ser útiles para organizar los bits de código relacionados en colecciones con nombre, incluso si solo planea llamarlos una vez.

Considerar:

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

Aunque solo se llama una vez a `calculateFinalPurchaseAmount(..)`, la organización de su comportamiento en una función con nombre separado hace que el código que usa su lógica (la sentencia `amount = calculateFinal...`) sea más limpio. Si la función tuviera más declaraciones, los beneficios serían aún más pronunciados.

### Scope

Si le pide a la empleada de la tienda telefónica un modelo de teléfono que su tienda no tiene, no podrá venderle el teléfono que desea. Ella solo tiene acceso a los teléfonos en el inventario de su tienda. Tendrá que probar en otra tienda para ver si puede encontrar el teléfono que está buscando.

La programación tiene un término para este concepto: *scope* (técnicamente llamado *lexical scope*). En JavaScript, cada función tiene su propio alcance. El alcance es básicamente una colección de variables, así como las reglas sobre cómo se accede a esas variables por nombre. Solo el código dentro de esa función puede acceder a las variables de *scope* de esa función.

Un nombre de variable debe ser único dentro del mismo ámbito; no puede haber dos variables `a` diferentes situadas una al lado de la otra. Pero el mismo nombre de variable `a` podría aparecer en diferentes ámbitos.

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

Además, un alcance puede ser anidado dentro de otro alcance, como si un payaso en una fiesta de cumpleaños hace estallar un globo dentro de otro globo. Si un ámbito está anidado dentro de otro, el código dentro del ámbito más interno puede acceder a las variables desde cualquier ámbito.

Considerar:

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

Las reglas de alcance léxico dicen que el código en un alcance puede acceder a variables de ese alcance o de cualquier alcance fuera de él.

Entonces, el código dentro de la función `inner()` tiene acceso a ambas variables `a` y `b`, pero el código en `outer()` tiene acceso solo a `a` - no puede acceder a `b` porque esa variable está solo dentro de `inner()`.

Recuerde este fragmento de código de antes:

```js
const TAX_RATE = 0.08;

function calculateFinalPurchaseAmount(amt) {
	// calculate the new amount with the tax
	amt = amt + (amt * TAX_RATE);

	// return the new amount
	return amt;
}
```

La constante `TAX_RATE` (variable) es accesible desde dentro de la función `calculateFinalPurchaseAmount(..)`, aunque no la pasamos, debido al lexical scope.

**Nota:** Para obtener más información sobre el lexical scope, consulte los primeros tres capítulos del título *Scope & Closures* de esta serie.

## Práctica

No hay absolutamente ningún sustituto para la práctica en el aprendizaje de la programación. Ninguna cantidad de escritura articulada de mi parte va a convertirte en un programador.

Con esto en mente, intentemos practicar algunos de los conceptos que aprendimos aquí en este capítulo. Daré los "requisitos", y tú lo intentas primero. Luego consulte el código que figura a continuación para ver cómo lo abordé.

* Escriba un programa para calcular el precio total de la compra de su teléfono. Seguirá comprando teléfonos (pista: ¡bucle!) Hasta que se quede sin dinero en su cuenta bancaria. También comprará accesorios para cada teléfono siempre que el monto de su compra esté por debajo de su límite de gasto mental.
* Una vez que haya calculado el monto de su compra, agregue el impuesto, luego imprima el monto de compra calculado, con el formato correcto.
* Finalmente, verifique el monto con el saldo de su cuenta bancaria para ver si puede pagarlo o no.
* Debe configurar algunas constantes para la "tax rate", "phone price", "accessory price" y "spending threshold", así como una variable para su "bank account balance".
* Debe definir funciones para calcular el impuesto y para dar formato al precio con un "$" y redondear a dos decimales.
* **Bonus Challenge:** Intente incorporar entradas en este programa, tal vez con el `prompt(..)` cubierto en "Input" anteriormente. Puede solicitar al usuario el saldo de su cuenta bancaria, por ejemplo. ¡Diviértete y sé creativo!

OK, adelante. Intentalo. ¡No mires el listado de mi código hasta que no lo hayas probado!

**Nota:** Debido a que este es un libro de JavaScript, obviamente voy a resolver el ejercicio de práctica en JavaScript. Pero puede hacerlo en otro idioma por ahora si se siente más cómodo.

Aquí está mi solución de JavaScript para este ejercicio:

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

**Nota:** La forma más sencilla de ejecutar este programa de JavaScript es escribirlo en la consola del desarrollador de su navegador más cercano.

¿Como hiciste? No estaría de más intentarlo de nuevo ahora que has visto mi código. Y juegue un poco cambiando algunas de las constantes para ver cómo se ejecuta el programa con diferentes valores.

## Revisión

Aprender programación no tiene que ser un proceso complejo y abrumador. Hay solo algunos conceptos básicos que necesita para envolver su cabeza.

Estos actúan como bloques de construcción. Para construir una torre alta, debes comenzar poniendo el bloque en la parte superior del bloque en la parte superior del bloque. Lo mismo ocurre con la programación. Aquí están algunos de los bloques de construcción de programación esenciales:

* Necesitas *operadores* para realizar acciones sobre valores.
* Necesitas *valores y tipos* para realizar diferentes tipos de acciones como matemáticas en `number` o salida con `string`.
* Necesita *variables* para almacenar datos (también conocido como *estado*) durante la ejecución de su programa.
* Necesitas *condicionales* como declaraciones `if` para tomar decisiones.
* Necesitas *bucles* para repetir tareas hasta que una condición deje de ser cierta.
* Necesita *funciones* para organizar su código en fragmentos lógicos y reutilizables.

Los comentarios de código son una forma efectiva de escribir código más legible, lo que hace que su programa sea más fácil de entender, mantener y corregir más adelante si hay problemas.

Finalmente, no descuides el poder de la práctica. La mejor manera de aprender cómo escribir código es escribir código.

Estoy emocionado de que estés bien encaminado para aprender a codificar, ¡ahora! Seguid así. No olvide consultar otros recursos de programación para principiantes (libros, blogs, capacitación en línea, etc.). Este capítulo y este libro son un gran comienzo, pero son solo una breve introducción.

El siguiente capítulo revisará muchos de los conceptos de este capítulo, pero desde una perspectiva más específica de JavaScript, que destacará la mayoría de los temas principales que se abordan con mayor detalle a lo largo del resto de la serie.
