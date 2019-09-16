# You Don't Know JS: Scope & Closures
# Chapter 1: ¿Qué es el Scope?

Uno de los paradigmas más fundamentales de casi todos los lenguajes de programación es la capacidad de almacenar valores en variables y luego recuperarlos o modificarlos. De hecho, la capacidad de almacenar valores y extraer valores de las variables es lo que da un *estado* de programa.

Sin ese concepto, un programa podría realizar algunas tareas, pero serían extremadamente limitadas y no terriblemente interesantes.

Pero la inclusión de variables en nuestro programa genera las preguntas más interesantes que abordaremos ahora: ¿dónde *viven* esas variables? En otras palabras, ¿dónde se almacenan? Y, lo más importante, ¿cómo los encuentra nuestro programa cuando las necesita?

Estas preguntas hablan de la necesidad de un conjunto bien definido de reglas para almacenar variables en algún lugar y para encontrar esas variables en un momento posterior. Llamaremos a ese conjunto de reglas: *Scope* (alcance).

Pero, ¿dónde y cómo se establecen estas reglas de *Scope*?

## Teoría del compilador

Puede ser evidente, o puede ser sorprendente, dependiendo de su nivel de interacción con varios lenguajes, pero a pesar del hecho de que JavaScript cae dentro de la categoría general de lenguajes "dinámicos" o "interpretados", de hecho es un lenguaje compilado. *No* se compila con suficiente antelación, como lo son muchos lenguajes compilados tradicionalmente, ni los resultados de la compilación son portátiles entre varios sistemas distribuidos.

Pero, sin embargo, el motor de JavaScript realiza muchos de los mismos pasos, aunque de maneras más sofisticadas de lo que comúnmente conocemos, de cualquier compilador de lenguaje tradicional.

En un proceso tradicional de lenguaje compilado, un trozo de código fuente, su programa, generalmente se someterá a tres pasos *antes* de ejecutarse, más o menos llamado "compilación":

1. **Tokenizing/Lexing:** separando una cadena de caracteres en fragmentos significativos (para el lenguaje), llamados tokens. Por ejemplo, considere el programa: `var a = 2;`. Es probable que este programa se divida en los siguientes tokens: `var`,` a`, `=`, `2` y`; `. El espacio en blanco puede o no persistir como un token, dependiendo de si es significativo o no.

     **Nota:** La diferencia entre tokenizing y lexing es sutil y académica, pero se centra en si estos tokens se identifican o no de manera *stateless* o *stateful*. En pocas palabras, si el tokenizador invocara reglas de análisis con estado para determinar si `a` debe considerarse un token distinto o solo parte de otro token, *eso* sería **lexing**.

2. **Parsing:** tomando una secuencia (array) de tokens y convirtiéndola en un árbol de elementos anidados, que representan colectivamente la estructura gramatical del programa. Este árbol se llama "AST" (<b>A</b>bstract <b>S</b>yntax <b>T</b>ree).

     El árbol para `var a = 2;` podría comenzar con un nodo de nivel superior llamado `VariableDeclaration`, con un nodo hijo llamado` Identifier` (cuyo valor es `a`), y otro hijo llamado` AssignmentExpression` que tiene un hijo llamado `NumericLiteral` (cuyo valor es` 2`).

3. **Code-Generation:** el proceso de tomar un AST y convertirlo en código ejecutable. Esta parte varía mucho según el idioma, la plataforma a la que se dirige, etc.

     Entonces, en lugar de atascarnos en detalles, simplemente saludaremos con la mano y diremos que hay una manera de tomar nuestro AST descrito anteriormente para `var a = 2;` y convertirlo en un conjunto de instrucciones de máquina para realmente *crear* una variable llamado `a` (incluida la reserva de memoria, etc.), y luego almacena un valor en `a`.

     **Nota:** Los detalles de cómo el motor gestiona los recursos del sistema son más profundos de lo que cavaremos, por lo que daremos por sentado que el motor puede crear y almacenar variables según sea necesario.

El motor de JavaScript es mucho más complejo que *solo* esos tres pasos, como lo son la mayoría de los compiladores de otros lenguajes. Por ejemplo, en el proceso de análisis y generación de código, ciertamente hay pasos para optimizar el rendimiento de la ejecución, incluido el colapso de elementos redundantes, etc.

Entonces, estoy pintando solo con trazos amplios aquí. Pero creo que verá en breve por qué *estos* detalles que *cubrimos*, incluso a un nivel alto, son relevantes.

Por un lado, los motores de JavaScript no tienen el lujo (como otros compiladores de lenguajes) de tener mucho tiempo para optimizar, porque la compilación de JavaScript no ocurre en un paso de compilación antes, como ocurre con otros lenguajes.

Para JavaScript, la compilación que ocurre, en muchos casos, solo microsegundos (¡o menos!) antes de que se ejecute el código. Para garantizar el rendimiento más rápido, los motores JS utilizan todo tipo de trucos (como los JIT, que compilan de forma diferida e incluso la compilación en caliente, etc.) que están más allá del "alcance" de nuestra discusión aquí.

Digamos, por simplicidad, que cualquier fragmento de JavaScript debe compilarse antes (¡generalmente *justo* antes!) Para que se ejecute. Entonces, el compilador JS tomará el programa `var a = 2;` y lo compilará *primero*, y luego estará listo para ejecutarlo, generalmente de inmediato.

## Entendiendo el Scope

La forma en que abordaremos el aprendizaje sobre el alcance es pensar en el proceso en términos de una conversación. Pero, ¿*quién* está teniendo la conversación?

### The Cast

Conozcamos al elenco de personajes que interactúan para procesar el programa `var a = 2;`, entonces entendemos sus conversaciones que escucharemos en breve:

1. *Engine*: responsable de la compilación y ejecución de principio a fin de nuestro programa JavaScript.

2. *Compiler*: uno de los amigos de *Engine*; maneja todo el trabajo sucio de análisis y generación de código (ver sección anterior).

3. *Scope*: otro amigo de *Engine*; recopila y mantiene una lista de búsqueda de todos los identificadores (variables) declarados, y aplica un estricto conjunto de reglas sobre cómo son accesibles para el código que se está ejecutando actualmente.

Para que comprenda completamente cómo funciona JavaScript, debe comenzar a *pensar* como lo hace *Engine* (y sus amigos), hacer las preguntas que hacen y responder esas preguntas de la misma manera.

### Back & Forth

Cuando vea el programa `var a = 2;`, lo más probable es que piense en eso como una declaración. Pero no es así como lo ve nuestro nuevo amigo *Engine*. De hecho, *Engine* ve dos declaraciones distintas, una que *Compiler* manejará durante la compilación y otra que *Engine* manejará durante la ejecución.

Entonces, analicemos cómo *Engine* y sus amigos abordarán el programa `var a = 2;`.

Lo primero que *Compiler* hará con este programa es realizar lexing para descomponerlo en tokens, que luego se analizarán en un árbol. Pero cuando *Compiler* llega a la generación de código, tratará este programa de manera algo diferente de lo que quizás se supone.

Una suposición razonable sería que *Compiler* producirá código que podría resumirse con este pseudocódigo: "Asignar memoria para una variable, etiquetarla como `a`, luego pegar el valor `2` en esa variable". Desafortunadamente, eso no es del todo exacto.

*Compiler* en su lugar procederá así:

1. Al encontrar `var a`, *Compiler* pregunta *Scope* para ver si ya existe una variable `a` para esa colección de alcances en particular. Si es así, *Compiler* ignora esta declaración y continúa. De lo contrario, *Compiler* le pide a *Scope* que declare una nueva variable llamada `a` para esa colección de alcances.

2. *Compiler* produce código para *Engine* para luego ejecutarlo, para manejar la asignación `a = 2`. El código *Engine* ejecuta primero preguntará *Scope* si hay una variable llamada `a` accesible en la colección de alcance actual. Si es así, *Engine* usa esa variable. De lo contrario, *Engine* busca *en otra parte* (consulte la sección *Scope* a continuación).

Si *Engine* finalmente encuentra una variable, le asigna el valor `2`. De lo contrario, *Engine* levantará la mano y gritará un error.

Para resumir: se toman dos acciones distintas para una asignación de variable: Primero, *Compiler* declara una variable (si no se declaró previamente en el alcance actual), y segundo, cuando se ejecuta, *Engine* busca la variable en *Scope* y se le asigna, si se encuentra.

### El compilador habla

Necesitamos un poco más de terminología del compilador para continuar con la comprensión.

Cuando *Engine* ejecuta el código que *Compiler* produjo para el paso (2), tiene que buscar la variable `a` para ver si se ha declarado, y esta consulta está consultando *Scope*. Pero el tipo de búsqueda que *Engine* realiza afecta el resultado de la búsqueda.

En nuestro caso, se dice que *Engine* estaría realizando una búsqueda "LHS" para la variable `a`. El otro tipo de búsqueda se llama "RHS".

Apuesto a que puedes adivinar lo que significan "L" y "R". Estos términos significan "Left-hand Side" y "Right-hand Side".

Lado ... de qué? **De una operación de asignación.**

En otras palabras, una búsqueda de LHS se realiza cuando aparece una variable en el lado izquierdo de una operación de asignación, y una búsqueda de RHS cuando aparece una variable en el lado derecho de una operación de asignación.

En realidad, seamos un poco más precisos. Una búsqueda de RHS es indistinguible, para nuestros propósitos, de simplemente una búsqueda del valor de alguna variable, mientras que la búsqueda de LHS está tratando de encontrar el contenedor de la variable en sí, para que pueda asignar. De esta manera, RHS *realmente* no significa "lado derecho de una tarea", más exactamente, significa "no lado izquierdo".

Siendo un poco simplista por un momento, también podría pensar que "RHS" en su lugar significa "recuperar su fuente (valor)", lo que implica que RHS significa "ir a obtener el valor de ...".

Vamos a profundizar en eso más.

Cuando yo digo:

```js
console.log( a );
```

La referencia a `a` es una referencia RHS, porque aquí no se asigna nada a `a`. En cambio, estamos buscando recuperar el valor de `a`, para que el valor pueda pasarse a `console.log (..) `.

Por el contrario:

```js
a = 2;
```

La referencia a `a` aquí es una referencia de LHS, porque en realidad no nos importa cuál es el valor actual, simplemente queremos encontrar la variable como objetivo para la operación de asignación `= 2`.

**Nota:** LHS y RHS que significan "lado izquierdo/derecho de una tarea" no significa necesariamente "lado izquierdo/derecho del operador de asignación `=`. Hay varias otras formas en que las tareas suceden, por lo que es mejor pensar conceptualmente sobre esto como: "quién es el objetivo de la tarea (LHS)" y "quién es la fuente de la tarea (RHS)".

Considere este programa, que tiene referencias tanto de LHS como de RHS:

```js
function foo(a) {
	console.log( a ); // 2
}

foo( 2 );
```

La última línea que invoca a `foo(..)` como llamada a una función requiere una referencia de RHS a `foo`, que significa "busca el valor de `foo` y dámelo". Además, `(..)` significa que el valor de `foo` debe ejecutarse, ¡así que será mejor que sea una función!

Hay una tarea sutil pero importante aquí. **¿Lo viste?**

Es posible que haya perdido el `a = 2` implícito en este fragmento de código. Ocurre cuando el valor `2` se pasa como argumento a la función `foo(..)`, en cuyo caso el valor `2` se **asigna** al parámetro `a`. Para (implícitamente) asignar al parámetro `a`, se realiza una búsqueda de LHS.

También hay una referencia RHS para el valor de `a`, y ese valor resultante se pasa a `console.log (..)`. `console.log (..)` necesita una referencia para ejecutarse. Es una búsqueda de RHS para el objeto `console`, luego se produce una resolución de propiedad para ver si tiene un método llamado `log`.

Finalmente, podemos conceptualizar que hay un intercambio LHS/RHS de pasar el valor `2` (por medio de la búsqueda de RHS de la variable `a`) en `log(..)`. Dentro de la implementación nativa de `log(..)`, podemos suponer que tiene parámetros, el primero de los cuales (quizás llamado `arg1`) tiene una búsqueda de referencia de LHS, antes de asignarle `2`.

**Nota:** Puede verse tentado a conceptualizar la declaración de función `function foo(a) {...` como una declaración y asignación de variable normal, como `var foo` y `foo = function (a) {. ..`. Al hacerlo, sería tentador pensar que esta declaración de función implica una búsqueda de LHS.

Sin embargo, la diferencia sutil pero importante es que *Compiler* maneja tanto la declaración como la definición del valor durante la generación del código, de modo que cuando *Engine* está ejecutando el código, no hay procesamiento necesario para "asignar" un valor de función a `foo` . Por lo tanto, no es realmente apropiado pensar en una declaración de función como una asignación de búsqueda de LHS en la forma en que las estamos discutiendo aquí.

### Engine/Scope Conversation

```js
function foo(a) {
	console.log( a ); // 2
}

foo( 2 );
```

Imaginemos el intercambio anterior (que procesa este fragmento de código) como una conversación. La conversación sería algo así:

> ***Engine***: Hola *Scope*, tengo una referencia RHS para `foo`. ¿Has oído hablar de eso?

> ***Scope***: Si, *Compiler* lo declaró hace solo un segundo. Es una función. Aqui tienes.

> ***Engine***: ¡Genial, gracias! OK, estoy ejecutando `foo`.

> ***Engine***: Oye, *Scope*, tengo una referencia de LHS para `a`, ¿alguna vez escuchaste de ella?

> ***Scope***: Si. *Compiler* lo declaró como un parámetro formal para `foo` recientemente. Aqui tienes.

> ***Engine***: Útil como siempre, *Scope*. Gracias de nuevo. Ahora, es hora de asignar `2` a `a`.

> ***Engine***: Oye, *Scope*, lamento molestarte de nuevo. Necesito una búsqueda RHS para `consola`. ¿Has oído hablar de eso?

> ***Scope***: No hay problema, *Engine*, esto es lo que hago todo el día. Sí, tengo `consola`. Él está incorporado. Aqui tienes.

> ***Engine***: Perfecto. Mirando hacia arriba `log (..)`. OK, genial, es una función.

> ***Engine***: Yo, *Scope*. ¿Me pueden ayudar con una referencia de RHS a `a`? Creo que lo recuerdo, pero solo quiero verificarlo dos veces.

> ***Scope***: Tienes razón, *Engine*. El mismo tipo, no ha cambiado. Aqui tienes.

> ***Engine***: Genial. Pasar el valor de `a`, que es `2`, a `log(..)`.

> ...

### Quiz

Comprueba tu comprensión hasta ahora. Asegúrese de jugar el papel de *Engine* y tener una "conversación" con el *Scope*:

```js
function foo(a) {
	var b = a;
	return a + b;
}

var c = foo( 2 );
```

1. Identifique todas las búsquedas de LHS (¡hay 3!).

2. Identifique todas las búsquedas de RHS (¡hay 4!).

**Nota:** ¡Vea la revisión del capítulo para las respuestas del cuestionario!

## Nested Scope

Dijimos que *Scope* es un conjunto de reglas para buscar variables por su nombre de identificador. Sin embargo, generalmente hay más de un *Scope* a considerar.

Así como un bloque o función está anidado dentro de otro bloque o función, los scopes (ámbitos) están anidados dentro de otros scopes. Por lo tanto, si no se puede encontrar una variable en el alcance inmediato, *Engine* consulta el siguiente alcance que contiene el exterior, continuando hasta que se encuentre o hasta que se alcance el alcance más externo (también conocido como global).

Considerar:

```js
function foo(a) {
	console.log( a + b );
}

var b = 2;

foo( 2 ); // 4
```

La referencia RHS para `b` no se puede resolver dentro de la función` foo`, pero se puede resolver en el *Scope* que la rodea (en este caso, el global).

Entonces, revisando las conversaciones entre *Engine* y *Scope*, escucharíamos:

> ***Engine***: "Oye, *Scope* de `foo`, ¿has oído hablar de `b`? Tengo una referencia de RHS para ello."

> ***Scope***: "Nope, nunca he oído hablar de él. Ve a pescar"

> ***Engine***: "Hey, *Scope* fuera de `foo`, oh, tú eres el *Scope* global, está bien. ¿Alguna vez has oído hablar de `b`? Tengo una referencia de RHS para eso."

> ***Scope***: "Sí, claro que sí. Aquí tienes."

Las reglas simples para atravesar anidados *Scope* : *Engine* comienza en el *Scope* actualmente en ejecución, busca la variable allí, luego, si no se encuentra, continúa subiendo un nivel, y así sucesivamente. Si se alcanza el alcance global más externo, la búsqueda se detiene, ya sea que encuentre la variable o no.

### Building on Metaphors

Para visualizar el proceso de resolución anidada *Scope*, quiero que pienses en este edificio alto.

<img src = "fig1.png" width = "250">

El edificio representa el conjunto de reglas anidadas *Scope* de nuestro programa. El primer piso del edificio representa su *Scope* actualmente en ejecución, esté donde esté. El nivel superior del edificio es el *Scope* global.

Usted resuelve las referencias de LHS y RHS mirando su piso actual, y si no lo encuentra, tome el elevador al siguiente piso, mire allí, luego al siguiente, y así sucesivamente. Una vez que llegue al piso superior (el *Scope* global), encontrará lo que está buscando o no. Pero tienes que parar de todos modos.

## Errors

¿Por qué importa si lo llamamos LHS o RHS?

Debido a que estos dos tipos de búsquedas se comportan de manera diferente en las circunstancias en que la variable aún no se ha declarado (no se encuentra en ningún *Scope* consultado).

Considerar:

```js
function foo(a) {
	console.log( a + b );
	b = a;
}

foo( 2 );
```

Cuando la búsqueda de RHS se produce por `b` la primera vez, no se encontrará. Se dice que es una variable "no declarada", porque no se encuentra en el ámbito.

Si una búsqueda de RHS no logra encontrar una variable, en algún lugar de los *Scope*s anidados, el *Engine* arroja un `ReferenceError`. Es importante tener en cuenta que el error es del tipo `ReferenceError`.

Por el contrario, si *Engine* está realizando una búsqueda de LHS y llega al piso superior (*Scope* global) sin encontrarlo, y si el programa no se está ejecutando en "Strict Mode" [^ note-estricto modo], entonces el *Scope* global creará una nueva variable con ese nombre **en el alcance global**, y lo devolverá a *Engine*.

*"No, no había ninguno antes, pero fui útil y creé uno para ti".*

"Strict Mode" [^note-strictmode], que se agregó en ES5, tiene varios comportamientos diferentes del modo normal/relaxed/lazy. Uno de estos comportamientos es que no permite la creación automática/implícita de variables globales. En ese caso, no habría una variable global *Scope* para devolver de una búsqueda de LHS, y *Engine* arrojaría un `ReferenceError` similar al caso de RHS.

Ahora, si se encuentra una variable para una búsqueda de RHS, pero intenta hacer algo con su valor que es imposible, como intentar ejecutar como función un valor que no es función, o hacer referencia a una propiedad en un `null` o `undefined`, entonces *Engine* arroja un tipo diferente de error, llamado `TypeError`.

`ReferenceError` está relacionado con la resolución *Scope*, mientras que `TypeError` implica que la resolución *Scope* fue exitosa, pero que se intentó una acción ilegal/imposible contra el resultado.

## Review (TL;DR)

El alcance es el conjunto de reglas que determina dónde y cómo se puede buscar una variable (identificador). Esta búsqueda puede ser con el propósito de asignar a la variable, que es una referencia de LHS (lado izquierdo), o puede ser con el propósito de recuperar su valor, que es un RHS (lado derecho ) referencia.

Las referencias de LHS resultan de operaciones de asignación. Las asignaciones relacionadas con *Scope* pueden ocurrir con el operador `=` o pasando argumentos a (asignar a) parámetros de función.

JavaScript *Engine* primero compila el código antes de que se ejecute, y al hacerlo, divide declaraciones como `var a = 2;` en dos pasos separados:

1. Primero, `var a` para declararlo en ese *Scope*. Esto se realiza al principio, antes de la ejecución del código.

2. Más tarde, `a = 2` para buscar la variable (referencia LHS) y asignarla si se encuentra.

Las búsquedas de referencia de LHS y RHS comienzan en el *Scope* que se está ejecutando actualmente, y si es necesario (es decir, no encuentran lo que están buscando allí), avanzan hacia arriba en el *Scope* anidado, un alcance (piso) a la vez, buscando el identificador, hasta que llegan al global (piso superior) y se detienen, y lo encuentran o no lo hacen.

Las referencias de RHS no cumplidas provocan que se arroje `ReferenceError`s. Las referencias de LHS no cumplidas dan como resultado un global automático, creado implícitamente de ese nombre (si no está en "Modo estricto" [^ note-strictlymode]), o un `ReferenceError` (si está en" Modo estricto "[^ note-strictlymode]) .

1. First, `var a` to declare it in that *Scope*. This is performed at the beginning, before code execution.

2. Later, `a = 2` to look up the variable (LHS reference) and assign to it if found.

### Quiz Answers

```js
function foo(a) {
	var b = a;
	return a + b;
}

var c = foo( 2 );
```

1. Identifique todas las búsquedas de LHS (¡hay 3!).

	**`c = ..`, `a = 2` (implicit param assignment) and `b = ..`**

2. Identifique todas las búsquedas de RHS (¡hay 4!).

    **`foo(2..`, `= a;`, `a + ..` and `.. + b`**


[^note-strictmode]: MDN: [Strict Mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions_and_function_scope/Strict_mode)
