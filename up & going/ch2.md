# You Don't Know JS: Up & Going
# Chapter 2: Into JavaScript

## Contenido

* Values & Types
   * Objects
      * Arrays
      * Functions
   * Built-In Type Methods
   * Comparing Values
      * Coercion
      * Truthy & Falsy
      * Equality
      * Inequality
* Variables
   * Function Scopes
      * Hoisting
      * Nested Scopes
* Conditionals
* Strict Mode
* Functions As Values
   * Immediately Invoked Function Expressions (IIFEs)
   * Closure
      * Modules
* this Identifier
* Prototypes
* Old & New
   * Polyfilling
   * Transpiling
* Non-JavaScript
* Review

En el capítulo anterior, introduje los componentes básicos de la programación, como variables, bucles, condicionales y funciones. Por supuesto, todo el código mostrado ha sido en JavaScript. Pero en este capítulo, queremos centrarnos específicamente en las cosas que necesita saber sobre JavaScript para ponerse en marcha como desarrollador de JS.

En este capítulo presentaremos algunos conceptos que no se explorarán completamente hasta los siguientes libros *YDKJS*. Puede considerar este capítulo como una visión general de los temas tratados en detalle a lo largo del resto de esta serie.

Especialmente si eres nuevo en JavaScript, deberías pasar bastante tiempo revisando los conceptos y ejemplos de código aquí varias veces. Cualquier buena base se coloca ladrillo por ladrillo, así que no espere que lo comprenda de inmediato en todo el primer paso.

Su viaje para aprender profundamente JavaScript comienza aquí.

**Nota:** Como dije en el Capítulo 1, definitivamente debes probar todo este código mientras lees y trabajas en este capítulo. Tenga en cuenta que parte del código aquí asume las capacidades introducidas en la versión más reciente de JavaScript en el momento de escribir este artículo (comúnmente denominado "ES6" para la 6ta edición de ECMAScript, el nombre oficial de la especificación JS). Si está utilizando un navegador anterior, ES6, es posible que el código no funcione. Se debe utilizar una actualización reciente de un navegador moderno (como Chrome, Firefox o IE).

## Values & Types

Como afirmamos en el Capítulo 1, JavaScript ha escrito valores, no variables. Los siguientes tipos incorporados están disponibles:

* `string`
* `number`
* `boolean`
* `null` y `undefined`
* `object`
* `symbol` (nuevo en ES6)

JavaScript proporciona un operador `typeof` que puede examinar un valor y decirle qué tipo es:

```js
var a;
typeof a;				// "undefined"

a = "hello world";
typeof a;				// "string"

a = 42;
typeof a;				// "number"

a = true;
typeof a;				// "boolean"

a = null;
typeof a;				// "object" -- weird, bug (raro, error)

a = undefined;
typeof a;				// "undefined"

a = { b: "c" };
typeof a;				// "object"
```

El valor de retorno del operador `typeof` es siempre uno de seis (siete a partir de ES6! - el tipo "symbol") valores de cadena. Es decir, `typeof "abc"` devuelve `"string"`, no `string`.

Observe cómo en este fragmento la variable `a` contiene cada tipo diferente de valor, y que a pesar de las apariencias, `typeof a` no solicita el "tipo de `a`", sino el "tipo del valor actualmente en `a`". Sólo los valores tienen tipos en JavaScript; Las variables son simples contenedores para esos valores.

`typeof null` es un caso interesante, porque retorna de forma errante `"object"`, cuando esperas que devuelva `"null"`.

**Advertencia:** Este es un error de larga duración en JS, pero es probable que nunca se solucione. ¡Demasiado código en la Web depende del error y, por lo tanto, solucionarlo causaría muchos más errores!

Además, tenga en cuenta `a = undefined`. Estamos estableciendo explícitamente `a` en el valor` undefined`, pero eso no es diferente en el comportamiento de una variable que aún no tiene un valor establecido, como con la línea `var a;` en la parte superior del fragmento. Una variable puede llegar a este estado de valor "indefinido" de varias maneras diferentes, incluidas las funciones que no devuelven ningún valor y el uso del operador `void`.

### Objects

El tipo `object` se refiere a un valor compuesto en el que puede establecer propiedades (ubicaciones con nombre) para que cada una tenga sus propios valores de cualquier tipo. Este es quizás uno de los tipos de valor más útiles en todo JavaScript.

```js
var obj = {
	a: "hello world",
	b: 42,
	c: true
};

obj.a;		// "hello world"
obj.b;		// 42
obj.c;		// true

obj["a"];	// "hello world"
obj["b"];	// 42
obj["c"];	// true
```

Puede ser útil pensar en este valor `obj` visualmente:

<img src="fig4.png">

Se puede acceder a las propiedades con *notación de punto (dot notation)* (es decir, `obj.a`) o con *notación de corchete (bracket notation)* (es decir, `obj ["a"]`). La notación de puntos es más corta y generalmente más fácil de leer, y por lo tanto se prefiere cuando es posible.

La notación de corchetes es útil si tiene un nombre de propiedad que tiene caracteres especiales, como `obj ["hello world!"]` - estas propiedades a menudo se conocen como *keys* cuando se accede a través de la notación de corchetes. La notación `[ ]` requiere una variable (explicada a continuación) o un `string` *literal* (que debe estar envuelta en `" .. "` o `' .. '`).

Por supuesto, la notación de corchetes también es útil si desea acceder a una property/key pero el nombre se almacena en otra variable, como:

```js
var obj = {
	a: "hello world",
	b: 42
};

var b = "a";

obj[b];			// "hello world"
obj["b"];		// 42
```

**Nota:** Para obtener más información sobre los `object` de JavaScript, consulte el título *this & Object Prototypes* de esta serie, específicamente el Capítulo 3.

Hay un par de otros tipos de valores con los que comúnmente interactuarás en los programas de JavaScript: *array* y *function*. Pero en lugar de ser tipos incorporados adecuados, debe pensarse que se parecen más a subtipos: versiones especializadas del tipo `object`.

#### Arrays

Un array es un `object` que contiene valores (de cualquier tipo) no particularmente en properties/keys, sino en posiciones indexadas numéricamente. Por ejemplo:

```js
var arr = [
	"hello world",
	42,
	true
];

arr[0];			// "hello world"
arr[1];			// 42
arr[2];			// true
arr.length;		// 3

typeof arr;		// "object"
```

**Nota:** Los lenguajes que comienzan a contar desde cero, como JS, usan `0` como el índice del primer elemento en el array.

Puede ser útil pensar en `arr` visualmente:

<img src="fig5.png">

Como los arrays son objetos especiales (como implica `typeof`), también pueden tener propiedades, por ejemplo la propiedad` length` que se actualiza automáticamente.

Teóricamente, podría usar un array como un objeto normal con sus propias propiedades nombradas, o podría usar un `object` pero solo asignarle propiedades numéricas (`0`, `1`, etc.) similares a un array. Sin embargo, esto generalmente se consideraría un uso inadecuado de los tipos respectivos.

El mejor y más natural enfoque es usar arrays para valores posicionados numéricamente y usar `object` para propiedades nombradas.

#### Functions

El otro subtipo `object` que usarás en todos tus programas JS es una función:

```js
function foo() {
	return 42;
}

foo.bar = "hello world";

typeof foo;			// "function"
typeof foo();		// "number"
typeof foo.bar;		// "string"
```

Nuevamente, las funciones son un subtipo de `objects` -- `typeof` devuelve `"function"`, lo que implica que una `function` es un tipo principal -- y, por lo tanto, puede tener propiedades, pero normalmente solo usará propiedades de objeto de función (como `foo.bar`) en casos limitados.

**Nota:** Para obtener más información sobre los valores de JS y sus tipos, consulte los dos primeros capítulos del título *Types & Grammar* de esta serie.

### Built-In Type Methods

Los tipos y subtipos integrados que acabamos de discutir tienen comportamientos expuestos como propiedades y métodos que son bastante poderosos y útiles.

Por ejemplo:

```js
var a = "hello world";
var b = 3.14159;

a.length;				// 11
a.toUpperCase();		// "HELLO WORLD"
b.toFixed(4);			// "3.1416"
```

El "cómo" detrás de poder llamar a `a.toUpperCase()` es más complicado que solo el método existente en el valor.

Brevemente, hay una forma de envoltura de objeto `String` (mayúscula `S`), típicamente llamada "native", que se empareja con el tipo primitivo `string`; es este contenedor de objetos el que define el método `toUpperCase()` en su prototype.

Cuando usa un valor primitivo como `"hello world"` como un `object` haciendo referencia a una propiedad o método (por ejemplo, `a.toUpperCase()` en el fragmento anterior), JS automáticamente "ajusta" el valor a su objeto contraparte de la envoltura (oculta bajo las cubiertas).

Un valor `string` puede ser wrapped por un objeto `String`, un `number` puede ser envuelto por un objeto` Number`, y un `boolean` puede ser envuelto por un objeto `Boolean`. En su mayor parte, no necesita preocuparse o usar directamente estas formas de envoltura de objetos de los valores; prefiera las formas de valores primitivos en prácticamente todos los casos y JavaScript se encargará del resto por usted.

**Nota:** Para obtener más información sobre los JS natives y "boxing,", consulte el Capítulo 3 del título *Types & Grammar* de esta serie. Para comprender mejor el prototype de un objeto, consulte el Capítulo 5 del título *this & Object Prototypes* de esta serie.

### Comparing Values

Hay dos tipos de comparaciones de valores principales que deberá realizar en sus programas JS: *equality* y *inequality*. El resultado de cualquier comparación es un valor estrictamente `booleano` (`true` o `false`), independientemente de qué tipos de valor se comparan.

#### Coercion

Hablamos brevemente sobre la coerción en el Capítulo 1, pero revisémoslo aquí.

Coercion viene en dos formas en JavaScript: *explicit* y *implicit*. La coerción explícita es simplemente la que puede ver en el código, que se producirá una conversión de un tipo a otro, mientras que la coerción implícita es cuando la conversión de tipo puede ocurrir como un efecto secundario no obvio de alguna otra operación.

Probablemente haya escuchado sentimientos como "la coerción es malvada" debido al hecho de que hay claramente lugares donde la coercion puede producir algunos resultados sorprendentes. Quizás nada evoca la frustración de los desarrolladores más que cuando el lenguaje los sorprende.

La coerción no es mala, ni tiene que ser sorprendente. De hecho, la mayoría de los casos que puede construir con coerción de tipo son bastante razonables y comprensibles, e incluso pueden utilizarse para *mejorar* la legibilidad de su código. Pero no profundizaremos en ese debate: el capítulo 4 del título *Types & Grammar* de esta serie abarca todos los lados.

Aquí hay un ejemplo de *explicit* coercion:

```js
var a = "42";

var b = Number( a );

a;				// "42"
b;				// 42 -- the number!
```

Y aquí hay un ejemplo de *implicit* coercion:

```js
var a = "42";

var b = a * 1;	// "42" implicitly coerced to 42 here

a;				// "42"
b;				// 42 -- the number!
```

#### Truthy & Falsy

En el Capítulo 1, mencionamos brevemente la naturaleza de los valores "truthy" y "falsy" : cuando un valor no `boolean` se convierte en un `boolean`, ¿se convierte en `true` o `false`, respectivamente?

La lista específica de valores "falsy" en JavaScript es la siguiente:

* `""` (empty string)
* `0`, `-0`, `NaN` (invalid `number`)
* `null`, `undefined`
* `false`

Cualquier valor que no esté en esta lista "falsy" es "truthy". Aquí hay algunos ejemplos:

* `"hello"`
* `42`
* `true`
* `[ ]`, `[ 1, "2", 3 ]` (arrays)
* `{ }`, `{ a: 42 }` (objects)
* `function foo() { .. }` (functions)

Es importante recordar que un valor non-`boolean` solo sigue esta "truthy"/"falsy" coercion si en realidad está obligada a un `boolean`. No es tan difícil confundirse con una situación que parece estar forzando un valor para un `boolean` cuando no lo es.

#### Equality

Hay cuatro operadores de igualdad: `==`, `===`, `!=` y `!==`. Las formas `!` son las versiones simétricas "not equal" de sus contrapartes; *non-equality* no debe confundirse con *inequality (desigualdad)*.

La diferencia entre `==` y `===` generalmente se caracteriza porque `==` verifica la igualdad de valores y `===` verifica la igualdad de valores y tipos. Sin embargo, esto es inexacto. La forma correcta de caracterizarlos es que `==` verifica la igualdad de valores con la coerción permitida, y `===` verifica la igualdad de valores sin permitir la coerción; `===` a menudo se llama "strict equality" por esta razón.

Considere la coerción implícita que está permitida por la comparación loose-equality `==` y no está permitida con la  `===` strict-equality:

```js
var a = "42";
var b = 42;

a == b;			// true
a === b;		// false
```

En la comparación `a == b`, JS se da cuenta de que los tipos no coinciden, por lo que pasa por una serie ordenada de pasos para forzar uno o ambos valores a un tipo diferente hasta que los tipos coincidan, donde entonces puede existir una simple igualdad de valores. 

Si lo piensas bien, hay dos formas posibles por las que `a == b` podría dar `true` a través de la coacción. O la comparación podría terminar como `42 == 42` o podría ser` "42" == "42" `. Entonces, ¿cuál es?

La respuesta: `"42"` se convierte en `42`, para hacer la comparación `42 == 42`. En un ejemplo tan simple, realmente no parece importar en qué sentido se va ese proceso, ya que el resultado final es el mismo. Hay casos más complejos en los que no solo importa cuál es el resultado final de la comparación, sino también cómo se obtiene.

El `a === b` produce `false`, porque la coacción no está permitida, por lo que la simple comparación de valores falla obviamente. Muchos desarrolladores creen que `===` es más predecible, por lo que abogan por usar siempre esa forma y mantenerse alejados de `==`. Creo que esta vista es muy miope. Creo que `==` es una herramienta poderosa que ayuda a tu programa, *si te tomas el tiempo para aprender cómo funciona*.

No vamos a cubrir todos los detalles esenciales de cómo funciona la coacción en las comparaciones `==` aquí. Gran parte de esto es bastante sensato, pero hay algunos casos importantes en las esquinas a tener en cuenta. Puede leer la sección 11.9.3 de la especificación ES5 (http://www.ecma-international.org/ecma-262/5.1/) para ver las reglas exactas, y se sorprenderá de lo sencillo que es este mecanismo, en comparación con todas las exageraciones negativas que lo rodean.

Para resumir una gran cantidad de detalles a unos pocos comentarios simples y ayudarlo a saber si debe usar `==` o `===` en varias situaciones, estas son mis reglas simples:

* Si cualquiera de los valores (a cada lado) en una comparación podría ser un valor `true` o `false`, evite `==` y use `===`.
* Si cualquiera de los valores en una comparación podría ser uno de estos valores específicos (`0`, `""`, o `[]`- array vacío), evite `==` y use `===`.
* En *todos* otros casos, es seguro usar `==`. No solo es seguro, sino que en muchos casos simplifica su código de una manera que mejora la legibilidad.

A lo que se reducen estas reglas, es necesario que piense críticamente sobre su código y sobre qué tipo de valores pueden venir a través de variables que se comparan para la igualdad. Si puede estar seguro de los valores y `==` es seguro, ¡úselo! Si no puede estar seguro de los valores, use `===`. Es así de simple.

Los pares `!=` non-equality con `==`, y `!==` con `===`. Todas las reglas y observaciones que acabamos de discutir son simétricas para estas comparaciones de no igualdad.

Debes tener en cuenta especialmente las reglas de comparación `==` y `===` si estás comparando dos valores no primitivos, como `object`  (incluyendo `function` y `array`). Debido a que esos valores se manejan por referencia, las comparaciones `==` y `===` simplemente verificarán si las referencias coinciden, nada sobre los valores subyacentes.

Por ejemplo, un `array` se coacciona por defecto a un `string` simplemente uniendo todos los valores con comas (`,`) entre ellos. Podrías pensar que dos `array` con el mismo contenido serían `==` iguales, pero no lo son:

```js
var a = [1,2,3];
var b = [1,2,3];
var c = "1,2,3";

a == c;		// true
b == c;		// true
a == b;		// false
```

**Nota:** Para obtener más información sobre las reglas de comparación de igualdad `==`, consulte la especificación ES5 (sección 11.9.3) y consulte también el Capítulo 4 del título *Types & Grammar* de esta serie; Consulte el Capítulo 2 para obtener más información sobre los valores en comparación con las referencias.

#### Inequality

Los operadores `<`, `>`, `<=` y `>=` se usan para la desigualdad, a la que se hace referencia en la especificación como "comparación relacional". Normalmente, se usarán con valores ordinariamente comparables como `number`. Es fácil de entender que `3 < 4`.

Pero los valores de `string` de JavaScript también se pueden comparar por la desigualdad, utilizando reglas alfabéticas típicas (`"bar" < "foo"`).

¿Qué pasa con la coacción? Reglas similares a la comparación `==` (¡aunque no exactamente idénticas!) Se aplican a los operadores de desigualdad. En particular, no hay operadores de "strict equality" que rechacen la coacción de la misma manera que lo hace `===`.

Considerar:

```js
var a = 41;
var b = "42";
var c = "43";

a < b;		// true
b < c;		// true
```

¿Qué pasa aquí? En la sección 11.8.5 de la especificación ES5, dice que si ambos valores en la comparación `<` son `string`, como ocurre con `b < c`, la comparación se realiza de forma lexicográfica (también conocida alfabéticamente como un diccionario). Pero si uno o ambos no son una `string`, como ocurre con `a < b`, ambos valores se convierten en `number` y se produce una comparación numérica típica.

El mayor problema que puede encontrar aquí con comparaciones entre tipos de valores potencialmente diferentes (recuerde, no hay formas de "strict inequality" para usar) es cuando uno de los valores no se puede convertir en un número válido, como:

```js
var a = 42;
var b = "foo";

a < b;		// false
a > b;		// false
a == b;		// false
```

Espera, ¿cómo pueden las tres comparaciones ser `false`? Debido a que el valor `b` se está coerced a un "invalid number value" `NaN` en las comparaciones `<` y `>`, y la especificación dice que `NaN` no es mayor ni menor que cualquier otro valor .

La comparación `==` falla por una razón diferente. `a == b` podría fallar si se interpreta como `42 == NaN` o `"42"=="foo"` - como explicamos anteriormente, el primero es el caso.

**Nota:** Para obtener más información sobre las reglas de comparación de desigualdad, consulte la sección 11.8.5 de la especificación ES5 y también consulte el Capítulo 4 del título *Types & Grammar* de esta serie.

## Variables

En JavaScript, los nombres de variables (incluidos los nombres de funciones) deben ser *identifiers* válidos. Las reglas estrictas y completas para los caracteres válidos en los identificadores son un poco complejas cuando se consideran caracteres no tradicionales, como Unicode. Sin embargo, si solo considera los caracteres alfanuméricos ASCII típicos, las reglas son simples.

Un identificador debe comenzar con `a`-`z`, `A`-`Z`, `$`, or `_`. Entonces puede contener cualquiera de esos caracteres más los números `0`-`9`.

En general, las mismas reglas se aplican a un nombre de propiedad como a un identificador de variable. Sin embargo, ciertas palabras no se pueden usar como variables, pero están bien como nombres de propiedades. Estas palabras se denominan "reserved words" e incluyen las palabras clave JS (`for`, `in`, `if`, etc.), así como `null`, `true` y `false`.

**Nota:** Para obtener más información sobre las palabras reservadas, consulte el Apéndice A del título *Types & Grammar* de esta serie.

### Function Scopes

Utiliza la palabra clave `var` para declarar una variable que pertenecerá al alcance de la función actual, o el alcance global si está en el nivel superior fuera de cualquier función.

#### Hoisting

Donde quiera que aparezca un `var` dentro de un alcance, se considera que esa declaración pertenece a todo el alcance y se puede acceder a ella en todas partes.

Metafóricamente, este comportamiento se denomina *hoisting (levantamiento/izar)*, cuando una declaración `var` se "mueve" conceptualmente a la parte superior de su ámbito de inclusión. Técnicamente, este proceso se explica con mayor precisión por la forma en que se compila el código, pero por ahora podemos omitir esos detalles.

Considerar:

```js
var a = 2;

foo();					// works because `foo()`
						// declaration is "hoisted"

function foo() {
	a = 3;

	console.log( a );	// 3

	var a;				// declaration is "hoisted"
						// to the top of `foo()`
}

console.log( a );	// 2
```

**Advertencia:** No es común o una buena idea confiar en la variable *hoisting (izar)* para usar una variable en su alcance antes de que aparece su declaración `var`; puede ser bastante confuso. Es mucho más común y aceptado el uso de *hoisted* en declaraciones de función, como hacemos con la llamada `foo()` que aparece antes de su declaración formal.

#### Nested Scopes

Cuando declara una variable, está disponible en cualquier parte de ese ámbito, así como en cualquier ámbito inferior/interior. Por ejemplo:

```js
function foo() {
	var a = 1;

	function bar() {
		var b = 2;

		function baz() {
			var c = 3;

			console.log( a, b, c );	// 1 2 3
		}

		baz();
		console.log( a, b );		// 1 2
	}

	bar();
	console.log( a );				// 1
}

foo();
```

Tenga en cuenta que `c` no está disponible dentro de `bar()`, porque se declara solo dentro del alcance interno `baz()`, y que `b` no está disponible para `foo()` por la misma razón.

Si intentas acceder al valor de una variable en un ámbito donde no está disponible, obtendrás un `ReferenceError` thrown. Si intenta establecer una variable que no se ha declarado, terminará creando una variable en el ámbito global de nivel superior (¡malo!) o recibirá un error, según el "strict mode" (consulte "Strict Mode"). Vamos a ver:

```js
function foo() {
	a = 1;	// `a` not formally declared
}

foo();
a;			// 1 -- oops, auto global variable :(
```

Esta es una muy mala práctica. No lo hagas Siempre declare formalmente sus variables.

Además de crear declaraciones para variables a nivel de función, ES6 *le permite* declarar que las variables pertenecen a bloques individuales (pares de `{ .. }`), usando la palabra clave `let`. Además de algunos detalles matizados, las reglas de alcance se comportarán aproximadamente de la misma forma que vimos con las funciones:

```js
function foo() {
	var a = 1;

	if (a >= 1) {
		let b = 2;

		while (b < 5) {
			let c = b * 2;
			b++;

			console.log( a + c );
		}
	}
}

foo();
// 5 7 9
```

Debido a que se usa `let` en lugar de `var`, `b` pertenecerá solo a la declaración `if` y, por lo tanto, no al alcance completo de la función `foo()`. De manera similar, `c` pertenece solo al bucle `while`. El ámbito del bloque es muy útil para administrar sus ámbitos variables de una manera más precisa, lo que puede hacer que su código sea mucho más fácil de mantener con el tiempo.

**Nota:** Para obtener más información sobre el alcance, consulte el título *Scope & Closures* de esta serie. Consulte el título *ES6 & Beyond* de esta serie para obtener más información sobre el alcance del bloque `let`.

## Conditionals

Además de la sentencia `if` que presentamos brevemente en el Capítulo 1, JavaScript proporciona algunos otros mecanismos condicionales que debemos analizar.

A veces, puede que te encuentres escribiendo una serie de afirmaciones `if..else..if` como esta:

```js
if (a == 2) {
	// do something
}
else if (a == 10) {
	// do another thing
}
else if (a == 42) {
	// do yet another thing
}
else {
	// fallback to here
}
```

Esta estructura funciona, pero es un poco detallada porque debe especificar la prueba `a` para cada caso. Aquí hay otra opción, la sentencia `switch`:

```js
switch (a) {
	case 2:
		// do something
		break;
	case 10:
		// do another thing
		break;
	case 42:
		// do yet another thing
		break;
	default:
		// fallback to here
}
```

El `break` es importante si desea que solo se ejecuten las declaraciones en un `case`. Si omite `break` de un `case`, y ese `case` coincide o se ejecuta, la ejecución continuará con las siguientes afirmaciones de `case` independientemente de la coincidencia de `case`. Esto se llama "fall through (caída a través)" es a veces útil/deseado:

```js
switch (a) {
	case 2:
	case 10:
		// some cool stuff
		break;
	case 42:
		// other stuff
		break;
	default:
		// fallback
}
```

Aquí, si `a` es `2` o `10`, ejecutará las declaraciones de código de "some cool stuff".

Otra forma de condicional en JavaScript es el "conditional operator", a menudo llamado "ternary operator". Es como una forma más concisa de una sola declaración `if..else`, como:

```js
var a = 42;

var b = (a > 41) ? "hello" : "world";

// similar to:

// if (a > 41) {
//    b = "hello";
// }
// else {
//    b = "world";
// }
```

Si la expresión de prueba (`a > 41` aquí) se evalúa como `true`, se genera la primera cláusula (`"hello"`), de lo contrario se genera la segunda cláusula (`"world"`), y cualquiera que sea el resultado, se asigna a `b`.

El operador condicional no tiene que ser usado en una asignación, pero ese es definitivamente el uso más común.

**Nota:** Para obtener más información sobre las condiciones de prueba y otros patrones para `switch` y `? :`, vea el título *Types & Grammar* de esta serie.

## Strict Mode

ES5 agregó un "strict mode" al lenguaje, que refuerza las reglas para ciertos comportamientos. En general, se considera que estas restricciones mantienen el código en un conjunto de pautas más seguro y apropiado. Además, seguir el modo estricto hace que su código sea generalmente más optimizable por el motor. El modo estricto es una gran ganancia para el código, y debe usarlo para todos sus programas.

Puede optar por el modo estricto para una función individual o un archivo completo, dependiendo de dónde coloque el modo estricto:

```js
function foo() {
	"use strict";

	// this code is strict mode

	function bar() {
		// this code is strict mode
	}
}

// this code is not strict mode
```

Compara eso con:

```js
"use strict";

function foo() {
	// this code is strict mode

	function bar() {
		// this code is strict mode
	}
}

// this code is strict mode
```

Una diferencia clave (¡mejora!) con el modo estricto es no permitir que la declaración implícita de la variable auto-global omita el `var`:

```js
function foo() {
	"use strict";	// turn on strict mode
	a = 1;			// `var` missing, ReferenceError
}

foo();
```

Si activa el modo estricto en su código y recibe errores, o el código comienza a comportarse con errores, su tentación podría ser evitar el modo estricto. Pero ese instinto sería una mala idea para disfrutar. Si el modo estricto causa problemas en su programa, es casi seguro que es una señal de que tiene cosas en su programa que debe corregir.

El modo estricto no solo mantendrá su código en una ruta más segura, y no solo hará que su código sea más optimizable, sino que también representa la dirección futura del idioma. Sería más fácil acostumbrarse al modo estricto ahora que seguir postergándolo; ¡solo será más difícil convertirlo más tarde!

**Nota:** Para obtener más información sobre el modo estricto, consulte el Capítulo 5 del título *Types & Grammar* de esta serie.

## Functions As Values

Hasta ahora, hemos analizado las funciones como el mecanismo principal de *scope* en JavaScript. Recuerda la sintaxis típica de la declaración de la función de la siguiente manera:

```js
function foo() {
	// ..
}
```

Aunque puede no parecer obvio a partir de esa sintaxis, `foo` es básicamente una variable en el ámbito de envolvente externo a la que se le da una referencia a la función que se está declarando. Es decir, la `function` en sí misma es un valor, como lo sería `42` o `[1,2,3]`.

Esto puede parecer un concepto extraño al principio, así que tómate un momento para reflexionar sobre ello. No solo puede pasar un valor (argumento) *a* una función, sino que *una función en sí misma puede ser un valor* que se asigna a las variables, o que se pasa o retorna de otras funciones.

Como tal, un valor de función debe considerarse como una expresión, al igual que cualquier otro valor o expresión.

Considerar:

```js
var foo = function() {
	// ..
};

var x = function bar(){
	// ..
};
```

La primera expresión de función asignada a la variable `foo` se llama *anonymous* porque no tiene `name`.

La segunda expresión de la función es *nombrada* (`bar`), incluso como referencia a ella también se asigna a la variable `x`. *Named function expressions* son generalmente más preferibles, aunque *anonymous function expressions* todavía son extremadamente comunes.

Para obtener más información, consulte el título de *Scope & Closures* de esta serie.

### Immediately Invoked Function Expressions (IIFEs)

En el fragmento anterior, ninguna de las expresiones de la función se ejecuta, podríamos si hubiéramos incluido `foo()` o `x()`, por ejemplo.

Hay otra forma de ejecutar una expresión de función, que normalmente se denomina como una expresión de función *immediately invoked function expression* (IIFE):

```js
(function IIFE(){
	console.log( "Hello!" );
})();
// "Hello!"
```

El outer `( .. )` externo que rodea a la expresión de la función `(function IIFE(){ .. })` es solo un matiz de la gramática JS necesaria para evitar que sea tratada como una declaración de función normal.

El `()` al final de la expresión - la línea `})();` - es lo que realmente ejecuta la expresión de función a la que se hace referencia inmediatamente antes.

Eso puede parecer extraño, pero no es tan extraño como a primera vista. Considera las similitudes entre `foo` y` IIFE` aquí:

```js
function foo() { .. }

// `foo` function reference expression,
// then `()` executes it
foo();

// `IIFE` function expression,
// then `()` executes it
(function IIFE(){ .. })();
```

Como puede ver, listar `(function IIFE(){ .. })` antes de ejecutar `()` es esencialmente lo mismo que incluir `foo` antes de ejecutar `()`; en ambos casos, la referencia de la función se ejecuta con `()` inmediatamente después.

Debido a que un IIFE es solo una función, y las funciones crean una variable *scope*, el uso de un IIFE de esta manera a menudo se usa para declarar variables que no afectarán el código circundante fuera del IIFE:

```js
var a = 42;

(function IIFE(){
	var a = 10;
	console.log( a );	// 10
})();

console.log( a );		// 42
```

Las IIFE también pueden tener valores de retorno:

```js
var x = (function IIFE(){
	return 42;
})();

x;	// 42
```

The `42` value gets `return`ed from the `IIFE`-named function being executed, and is then assigned to `x`.

El valor `42` que se obtiene gracias al `return` de la función `IIFE` que se ejecuta, y luego se asigna a `x`.

### Closure

*Closure* is one of the most important, and often least understood, concepts in JavaScript. I won't cover it in deep detail here, and instead refer you to the *Scope & Closures* title of this series. But I want to say a few things about it so you understand the general concept. It will be one of the most important techniques in your JS skillset.

You can think of closure as a way to "remember" and continue to access a function's scope (its variables) even once the function has finished running.

Consider:

```js
function makeAdder(x) {
	// parameter `x` is an inner variable

	// inner function `add()` uses `x`, so
	// it has a "closure" over it
	function add(y) {
		return y + x;
	};

	return add;
}
```

The reference to the inner `add(..)` function that gets returned with each call to the outer `makeAdder(..)` is able to remember whatever `x` value was passed in to `makeAdder(..)`. Now, let's use `makeAdder(..)`:

```js
// `plusOne` gets a reference to the inner `add(..)`
// function with closure over the `x` parameter of
// the outer `makeAdder(..)`
var plusOne = makeAdder( 1 );

// `plusTen` gets a reference to the inner `add(..)`
// function with closure over the `x` parameter of
// the outer `makeAdder(..)`
var plusTen = makeAdder( 10 );

plusOne( 3 );		// 4  <-- 1 + 3
plusOne( 41 );		// 42 <-- 1 + 41

plusTen( 13 );		// 23 <-- 10 + 13
```

More on how this code works:

1. When we call `makeAdder(1)`, we get back a reference to its inner `add(..)` that remembers `x` as `1`. We call this function reference `plusOne(..)`.
2. When we call `makeAdder(10)`, we get back another reference to its inner `add(..)` that remembers `x` as `10`. We call this function reference `plusTen(..)`.
3. When we call `plusOne(3)`, it adds `3` (its inner `y`) to the `1` (remembered by `x`), and we get `4` as the result.
4. When we call `plusTen(13)`, it adds `13` (its inner `y`) to the `10` (remembered by `x`), and we get `23` as the result.

Don't worry if this seems strange and confusing at first -- it can be! It'll take lots of practice to understand it fully.

But trust me, once you do, it's one of the most powerful and useful techniques in all of programming. It's definitely worth the effort to let your brain simmer on closures for a bit. In the next section, we'll get a little more practice with closure.

#### Modules

The most common usage of closure in JavaScript is the module pattern. Modules let you define private implementation details (variables, functions) that are hidden from the outside world, as well as a public API that *is* accessible from the outside.

Consider:

```js
function User(){
	var username, password;

	function doLogin(user,pw) {
		username = user;
		password = pw;

		// do the rest of the login work
	}

	var publicAPI = {
		login: doLogin
	};

	return publicAPI;
}

// create a `User` module instance
var fred = User();

fred.login( "fred", "12Battery34!" );
```

The `User()` function serves as an outer scope that holds the variables `username` and `password`, as well as the inner `doLogin()` function; these are all private inner details of this `User` module that cannot be accessed from the outside world.

**Warning:** We are not calling `new User()` here, on purpose, despite the fact that probably seems more common to most readers. `User()` is just a function, not a class to be instantiated, so it's just called normally. Using `new` would be inappropriate and actually waste resources.

Executing `User()` creates an *instance* of the `User` module -- a whole new scope is created, and thus a whole new copy of each of these inner variables/functions. We assign this instance to `fred`. If we run `User()` again, we'd get a new instance entirely separate from `fred`.

The inner `doLogin()` function has a closure over `username` and `password`, meaning it will retain its access to them even after the `User()` function finishes running.

`publicAPI` is an object with one property/method on it, `login`, which is a reference to the inner `doLogin()` function. When we return `publicAPI` from `User()`, it becomes the instance we call `fred`.

At this point, the outer `User()` function has finished executing. Normally, you'd think the inner variables like `username` and `password` have gone away. But here they have not, because there's a closure in the `login()` function keeping them alive.

That's why we can call `fred.login(..)` -- the same as calling the inner `doLogin(..)` -- and it can still access `username` and `password` inner variables.

There's a good chance that with just this brief glimpse at closure and the module pattern, some of it is still a bit confusing. That's OK! It takes some work to wrap your brain around it.

From here, go read the *Scope & Closures* title of this series for a much more in-depth exploration.

## `this` Identifier

Another very commonly misunderstood concept in JavaScript is the `this` identifier. Again, there's a couple of chapters on it in the *this & Object Prototypes* title of this series, so here we'll just briefly introduce the concept.

While it may often seem that `this` is related to "object-oriented patterns," in JS `this` is a different mechanism.

If a function has a `this` reference inside it, that `this` reference usually points to an `object`. But which `object` it points to depends on how the function was called.

It's important to realize that `this` *does not* refer to the function itself, as is the most common misconception.

Here's a quick illustration:

```js
function foo() {
	console.log( this.bar );
}

var bar = "global";

var obj1 = {
	bar: "obj1",
	foo: foo
};

var obj2 = {
	bar: "obj2"
};

// --------

foo();				// "global"
obj1.foo();			// "obj1"
foo.call( obj2 );		// "obj2"
new foo();			// undefined
```

There are four rules for how `this` gets set, and they're shown in those last four lines of that snippet.

1. `foo()` ends up setting `this` to the global object in non-strict mode -- in strict mode, `this` would be `undefined` and you'd get an error in accessing the `bar` property -- so `"global"` is the value found for `this.bar`.
2. `obj1.foo()` sets `this` to the `obj1` object.
3. `foo.call(obj2)` sets `this` to the `obj2` object.
4. `new foo()` sets `this` to a brand new empty object.

Bottom line: to understand what `this` points to, you have to examine how the function in question was called. It will be one of those four ways just shown, and that will then answer what `this` is.

**Note:** For more information about `this`, see Chapters 1 and 2 of the *this & Object Prototypes* title of this series.

## Prototypes

The prototype mechanism in JavaScript is quite complicated. We will only glance at it here. You will want to spend plenty of time reviewing Chapters 4-6 of the *this & Object Prototypes* title of this series for all the details.

When you reference a property on an object, if that property doesn't exist, JavaScript will automatically use that object's internal prototype reference to find another object to look for the property on. You could think of this almost as a fallback if the property is missing.

The internal prototype reference linkage from one object to its fallback happens at the time the object is created. The simplest way to illustrate it is with a built-in utility called `Object.create(..)`.

Consider:

```js
var foo = {
	a: 42
};

// create `bar` and link it to `foo`
var bar = Object.create( foo );

bar.b = "hello world";

bar.b;		// "hello world"
bar.a;		// 42 <-- delegated to `foo`
```

It may help to visualize the `foo` and `bar` objects and their relationship:

<img src="fig6.png">

The `a` property doesn't actually exist on the `bar` object, but because `bar` is prototype-linked to `foo`, JavaScript automatically falls back to looking for `a` on the `foo` object, where it's found.

This linkage may seem like a strange feature of the language. The most common way this feature is used -- and I would argue, abused -- is to try to emulate/fake a "class" mechanism with "inheritance."

But a more natural way of applying prototypes is a pattern called "behavior delegation," where you intentionally design your linked objects to be able to *delegate* from one to the other for parts of the needed behavior.

**Note:** For more information about prototypes and behavior delegation, see Chapters 4-6 of the *this & Object Prototypes* title of this series.

## Old & New

Some of the JS features we've already covered, and certainly many of the features covered in the rest of this series, are newer additions and will not necessarily be available in older browsers. In fact, some of the newest features in the specification aren't even implemented in any stable browsers yet.

So, what do you do with the new stuff? Do you just have to wait around for years or decades for all the old browsers to fade into obscurity?

That's how many people think about the situation, but it's really not a healthy approach to JS.

There are two main techniques you can use to "bring" the newer JavaScript stuff to the older browsers: polyfilling and transpiling.

### Polyfilling

The word "polyfill" is an invented term (by Remy Sharp) (https://remysharp.com/2010/10/08/what-is-a-polyfill) used to refer to taking the definition of a newer feature and producing a piece of code that's equivalent to the behavior, but is able to run in older JS environments.

For example, ES6 defines a utility called `Number.isNaN(..)` to provide an accurate non-buggy check for `NaN` values, deprecating the original `isNaN(..)` utility. But it's easy to polyfill that utility so that you can start using it in your code regardless of whether the end user is in an ES6 browser or not.

Consider:

```js
if (!Number.isNaN) {
	Number.isNaN = function isNaN(x) {
		return x !== x;
	};
}
```

The `if` statement guards against applying the polyfill definition in ES6 browsers where it will already exist. If it's not already present, we define `Number.isNaN(..)`.

**Note:** The check we do here takes advantage of a quirk with `NaN` values, which is that they're the only value in the whole language that is not equal to itself. So the `NaN` value is the only one that would make `x !== x` be `true`.

Not all new features are fully polyfillable. Sometimes most of the behavior can be polyfilled, but there are still small deviations. You should be really, really careful in implementing a polyfill yourself, to make sure you are adhering to the specification as strictly as possible.

Or better yet, use an already vetted set of polyfills that you can trust, such as those provided by ES5-Shim (https://github.com/es-shims/es5-shim) and ES6-Shim (https://github.com/es-shims/es6-shim).

### Transpiling

There's no way to polyfill new syntax that has been added to the language. The new syntax would throw an error in the old JS engine as unrecognized/invalid.

So the better option is to use a tool that converts your newer code into older code equivalents. This process is commonly called "transpiling," a term for transforming + compiling.

Essentially, your source code is authored in the new syntax form, but what you deploy to the browser is the transpiled code in old syntax form. You typically insert the transpiler into your build process, similar to your code linter or your minifier.

You might wonder why you'd go to the trouble to write new syntax only to have it transpiled away to older code -- why not just write the older code directly?

There are several important reasons you should care about transpiling:

* The new syntax added to the language is designed to make your code more readable and maintainable. The older equivalents are often much more convoluted. You should prefer writing newer and cleaner syntax, not only for yourself but for all other members of the development team.
* If you transpile only for older browsers, but serve the new syntax to the newest browsers, you get to take advantage of browser performance optimizations with the new syntax. This also lets browser makers have more real-world code to test their implementations and optimizations on.
* Using the new syntax earlier allows it to be tested more robustly in the real world, which provides earlier feedback to the JavaScript committee (TC39). If issues are found early enough, they can be changed/fixed before those language design mistakes become permanent.

Here's a quick example of transpiling. ES6 adds a feature called "default parameter values." It looks like this:

```js
function foo(a = 2) {
	console.log( a );
}

foo();		// 2
foo( 42 );	// 42
```

Simple, right? Helpful, too! But it's new syntax that's invalid in pre-ES6 engines. So what will a transpiler do with that code to make it run in older environments?

```js
function foo() {
	var a = arguments[0] !== (void 0) ? arguments[0] : 2;
	console.log( a );
}
```

As you can see, it checks to see if the `arguments[0]` value is `void 0` (aka `undefined`), and if so provides the `2` default value; otherwise, it assigns whatever was passed.

In addition to being able to now use the nicer syntax even in older browsers, looking at the transpiled code actually explains the intended behavior more clearly.

You may not have realized just from looking at the ES6 version that `undefined` is the only value that can't get explicitly passed in for a default-value parameter, but the transpiled code makes that much more clear.

The last important detail to emphasize about transpilers is that they should now be thought of as a standard part of the JS development ecosystem and process. JS is going to continue to evolve, much more quickly than before, so every few months new syntax and new features will be added.

If you use a transpiler by default, you'll always be able to make that switch to newer syntax whenever you find it useful, rather than always waiting for years for today's browsers to phase out.

There are quite a few great transpilers for you to choose from. Here are some good options at the time of this writing:

* Babel (https://babeljs.io) (formerly 6to5): Transpiles ES6+ into ES5
* Traceur (https://github.com/google/traceur-compiler): Transpiles ES6, ES7, and beyond into ES5

## Non-JavaScript

So far, the only things we've covered are in the JS language itself. The reality is that most JS is written to run in and interact with environments like browsers. A good chunk of the stuff that you write in your code is, strictly speaking, not directly controlled by JavaScript. That probably sounds a little strange.

The most common non-JavaScript JavaScript you'll encounter is the DOM API. For example:

```js
var el = document.getElementById( "foo" );
```

The `document` variable exists as a global variable when your code is running in a browser. It's not provided by the JS engine, nor is it particularly controlled by the JavaScript specification. It takes the form of something that looks an awful lot like a normal JS `object`, but it's not really exactly that. It's a special `object,` often called a "host object."

Moreover, the `getElementById(..)` method on `document` looks like a normal JS function, but it's just a thinly exposed interface to a built-in method provided by the DOM from your browser. In some (newer-generation) browsers, this layer may also be in JS, but traditionally the DOM and its behavior is implemented in something more like C/C++.

Another example is with input/output (I/O).

Everyone's favorite `alert(..)` pops up a message box in the user's browser window. `alert(..)` is provided to your JS program by the browser, not by the JS engine itself. The call you make sends the message to the browser internals and it handles drawing and displaying the message box.

The same goes with `console.log(..)`; your browser provides such mechanisms and hooks them up to the developer tools.

This book, and this whole series, focuses on JavaScript the language. That's why you don't see any substantial coverage of these non-JavaScript JavaScript mechanisms. Nevertheless, you need to be aware of them, as they'll be in every JS program you write!

## Review

The first step to learning JavaScript's flavor of programming is to get a basic understanding of its core mechanisms like values, types, function closures, `this`, and prototypes.

Of course, each of these topics deserves much greater coverage than you've seen here, but that's why they have chapters and books dedicated to them throughout the rest of this series. After you feel pretty comfortable with the concepts and code samples in this chapter, the rest of the series awaits you to really dig in and get to know the language deeply.

The final chapter of this book will briefly summarize each of the other titles in the series and the other concepts they cover besides what we've already explored.
