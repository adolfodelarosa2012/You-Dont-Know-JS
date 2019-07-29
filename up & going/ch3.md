# You Don't Know JS: Up & Going
# Chapter 3: Into YDKJS

¿De qué se trata esta serie? En pocas palabras, se trata de tomar en serio la tarea de aprender *todas las partes de JavaScript*, no solo un subconjunto del lenguaje que alguien llamó "the good parts", y no solo la cantidad mínima que necesita para hacer su trabajo en el trabajo.

Los desarrolladores serios en otros lenguajes esperan esforzarse por aprender la mayoría o todos los lenguaje(s) en los que escriben principalmente, pero los desarrolladores de JS parecen sobresalir de la multitud en el sentido de que generalmente no aprenden mucho el lenguaje. Esto no es algo bueno, y no es algo que debamos seguir permitiendo que sea la norma.

La serie *You Don't Know JS* (*YDKJS*) contrasta fuertemente con los enfoques típicos para aprender JS, y es diferente a casi cualquier otro libro de JS que leerá. Te desafía a ir más allá de tu zona de confort y a hacer preguntas más profundas sobre "por qué" para cada comportamiento que encuentres. ¿Estás preparado para ese desafío?

Voy a usar este capítulo final para resumir brevemente qué esperar del resto de los libros de la serie, y cómo hacer más eficazmente para construir una base de aprendizaje JS sobre *YDKJS*.

## Scope & Closures

Quizás una de las cosas más fundamentales que necesitará para aceptar rápidamente es cómo funciona realmente el scoping de las variables en JavaScript. No es suficiente tener creencias anecdóticas *difusas* sobre el scope.

El título de *Scope & Closures* comienza por desacreditar el error común de que JS es un "lenguaje interpretado" y, por lo tanto, no se compila. No

El motor JS compila su código justo antes de la ejecución (y, a veces, durante la ejecución). Por lo tanto, utilizamos una comprensión más profunda del enfoque del compilador a nuestro código para comprender cómo encuentra y maneja las declaraciones de variables y funciones. A lo largo del camino, vemos la metáfora típica de la gestión de alcance de variables de JS, "Hoisting (Elevación)".

Esta comprensión crítica del "lexical scope" es en lo que basamos nuestra exploración del closure para el último capítulo del libro. El closure es quizás el concepto más importante de todo JS, pero si no ha entendido bien cómo funciona el scope, es probable que el closure quede fuera de su alcance.

Una aplicación importante del closure es el module pattern, como lo presentamos brevemente en este libro en el Capítulo 2. El patrón de módulo es quizás el patrón de organización de código más frecuente en todo JavaScript; una profunda comprensión de esto debería ser una de tus más altas prioridades.

## this & Object Prototypes

Quizás uno de los errores más extendidos y persistentes sobre JavaScript es que la palabra clave `this` se refiere a la función en la que aparece. Terriblemente equivocada.

La palabra clave `this` está vinculada dinámicamente en función de cómo se ejecuta la función en cuestión, y resulta que hay cuatro reglas simples para comprender y determinar completamente la vinculación de `this`.

Muy relacionado con la palabra clave `this` está el mecanismo de prototipo de objeto, que es una cadena de búsqueda de propiedades, similar a cómo se encuentran las variables de alcance léxico. Pero envuelto en los prototipos está el otro gran error de JS: la idea de emular clases (falsas) y la herencia (llamada "prototypal").

Desafortunadamente, el deseo de llevar el pensamiento de patrones de diseño de herencia y clases a JavaScript es casi lo peor que podría intentar hacer, porque si bien la sintaxis puede engañarlo para que piense que hay algo como las clases presentes, de hecho, el mecanismo del prototipo es fundamentalmente opuesto en su comportamiento

Lo que está en cuestión es si es mejor ignorar el desajuste y pretender que lo que está implementando es "herencia", o si es más apropiado aprender y aceptar cómo funciona realmente el sistema prototipo de objeto. Este último se denomina más apropiadamente "delegación de comportamiento".

Esto es más que una preferencia sintáctica. La delegación es un patrón de diseño completamente diferente y más poderoso, que reemplaza la necesidad de diseñar con clases y herencia. Pero estas afirmaciones se irán en contra de casi cualquier otra publicación de blog, libro y conferencia sobre el tema durante toda la vida de JavaScript.

Las afirmaciones que hago con respecto a la delegación frente a la herencia no provienen de una aversión al lenguaje y su sintaxis, sino del deseo de ver la verdadera capacidad del lenguaje aprovechada adecuadamente y la interminable confusión y frustración borradas.

Pero el caso que hago con respecto a los prototipos y la delegación es mucho más complicado de lo que voy a consentir aquí. Si está listo para reconsiderar todo lo que cree saber sobre las "clases" y la "herencia" de JavaScript, le ofrezco la oportunidad de "tomar la píldora roja" (*Matrix* 1999) y consultar los Capítulos 4-6 de *this & Object Prototypes* título de esta serie.

## Types & Grammar

El tercer título de esta serie se centra principalmente en abordar otro tema muy controvertido: la coerción de tipos. Quizás ningún tema cause más frustración con los desarrolladores de JS que cuando se habla de las confusiones que rodean la coerción implícita.

De lejos, la sabiduría convencional es que la coerción implícita es una "parte mala" del lenguaje y debe evitarse a toda costa. De hecho, algunos han ido tan lejos como para llamarlo un "defecto" en el diseño del lenguaje. De hecho, hay herramientas cuyo trabajo completo es no hacer nada más que escanear su código y quejarse si está haciendo algo, incluso remotamente, como la coerción.

¿Pero es la coerción realmente tan confusa, tan mala, tan traicionera, que su código está condenado desde el principio si lo usa?

Yo digo que no. Después de haber comprendido cómo funcionan realmente los tipos y valores en los Capítulos 1-3, el Capítulo 4 aborda este debate y explica completamente cómo funciona la coerción, en todos sus rincones y grietas. Vemos qué partes de la coerción son realmente sorprendentes y qué partes realmente tienen sentido si se les da tiempo para aprender.

Pero no estoy simplemente sugiriendo que la coerción es sensata y fácil de aprender, estoy afirmando que la coerción es una herramienta increíblemente útil y totalmente subestimada que *debería estar usando en su código*. Estoy diciendo que la coerción, cuando se usa correctamente, no solo funciona, sino que mejora su código. Todos los detractores y escépticos seguramente se burlarán de tal posición, pero creo que es una de las principales claves para mejorar su juego JS.

¿Quieres seguir siguiendo lo que dice la multitud, o estás dispuesto a dejar de lado todos los supuestos y mirar la coerción con una nueva perspectiva? El título *Types & Grammar* de esta serie obligará a pensar.

## Async & Performance

Los primeros tres títulos de esta serie se centran en la mecánica central del lenguaje, pero el cuarto título se ramifica ligeramente para cubrir patrones además de la mecánica del lenguaje para administrar la programación asincrónica. La asincronía no solo es crítica para el rendimiento de nuestras aplicaciones, sino que se está convirtiendo cada vez más en *el* factor crítico en la capacidad de escritura y mantenimiento.

El libro comienza primero aclarando mucha terminología y confusión de conceptos en torno a cosas como "asíncrono", "paralelo" y "concurrente", y explica en profundidad cómo tales cosas se aplican y no se aplican a JS.

Luego pasamos a examinar las devoluciones de llamada como el método principal para habilitar la asincronía. Pero es aquí donde rápidamente vemos que la devolución de llamada por sí sola es irremediablemente insuficiente para las demandas modernas de la programación asincrónica. Identificamos dos deficiencias principales de la codificación solo de devolución de llamada: *Inversion of Control (Inversión de control)* (IoC) pérdida de confianza y falta de capacidad de razón lineal.

Para abordar estas dos deficiencias principales, ES6 introduce dos nuevos mecanismos (y de hecho, patrones): promises y generators.

Las promesas son una envoltura independiente del tiempo en torno a un "valor futuro", que le permite razonar y componerlas independientemente de si el valor está listo o no. Además, resuelven eficazmente los problemas de confianza de IoC al enrutar las devoluciones de llamada a través de un mecanismo de promesa confiable y componible.

Los generadores introducen un nuevo modo de ejecución para las funciones JS, mediante el cual el generador se puede pausar en los puntos de 'rendimiento' y se puede reanudar de forma asincrónica más tarde. La capacidad de pausa y reanudación permite que el código de búsqueda síncrono y secuencial en el generador se procese de forma asíncrona detrás de escena. Al hacerlo, abordamos las confusiones de salto de llamada no lineales y no locales y, por lo tanto, hacemos que nuestro código asíncrono se vea sincronizado para que sea más razonable.

Pero es la combinación de promesas y generadores lo que "produce" nuestro patrón de codificación asíncrono más efectivo hasta la fecha en JavaScript. De hecho, gran parte de la sofisticación futura de la asincronía que vendrá en ES7 y más adelante se construirá sobre esta base. Para tomar en serio la programación efectiva en un mundo asíncrono, necesitará sentirse realmente cómodo combinando promesas y generadores.

Si las promesas y los generadores tratan de expresar patrones que permiten que nuestros programas se ejecuten de manera más simultánea y, por lo tanto, logren más procesamiento en un período más corto, JS tiene muchas otras facetas de optimización del rendimiento que vale la pena explorar.

El Capítulo 5 profundiza en temas como el paralelismo de programas con Web Workers y el paralelismo de datos con SIMD, así como técnicas de optimización de bajo nivel como ASM.js. El Capítulo 6 analiza la optimización del rendimiento desde la perspectiva de las técnicas de evaluación comparativa adecuadas, incluido qué tipos de rendimiento deben preocuparse y qué ignorar.

Escribir JavaScript efectivamente significa escribir código que pueda romper las barreras de restricción de ser ejecutado dinámicamente en una amplia gama de navegadores y otros entornos. Se requiere mucha planificación y esfuerzo intrincado y detallado de nuestras partes para llevar un programa de "funciona" a "funciona bien".

El título *Async & Performance* está diseñado para brindarle todas las herramientas y habilidades que necesita para escribir un código JavaScript razonable y eficaz.

## ES6 & Beyond

No importa cuánto sientas que has dominado JavaScript hasta este punto, la verdad es que JavaScript nunca dejará de evolucionar y, además, la tasa de evolución está aumentando rápidamente. Este hecho es casi una metáfora del espíritu de esta serie, para aceptar que nunca *conoceremos* completamente cada parte de JS, porque tan pronto como lo domines todo, habrá nuevas cosas en el futuro. Necesitaré aprender.

Este título está dedicado tanto a las visiones a corto como a mediano plazo de hacia dónde se dirige el lenguaje, no solo a las cosas *conocidas* como ES6 sino a las cosas *probables* más allá.

Si bien todos los títulos de esta serie abarcan el estado de JavaScript en el momento de escribir este artículo, que se encuentra en la mitad de la adopción de ES6, el enfoque principal de la serie se ha centrado más en ES5. Ahora, queremos centrar nuestra atención en ES6, ES7 y ...

Dado que ES6 está casi completo en el momento de escribir este artículo, *ES6 y más allá* comienza dividiendo las cosas concretas del paisaje ES6 en varias categorías clave, que incluyen nueva sintaxis, nuevas estructuras de datos (colecciones) y nuevas capacidades de procesamiento y API. Cubrimos cada una de estas nuevas características de ES6, en diferentes niveles de detalle, incluida la revisión de detalles que se mencionan en otros libros de esta serie.

Algunas cosas interesantes de ES6 que esperamos leer: desestructuración, valores de parámetros predeterminados, símbolos, métodos concisos, propiedades calculadas, funciones de flecha, alcance de bloque, promesas, generadores, iteradores, módulos, proxies, mapas débiles y mucho, mucho más. ¡Uf, ES6 tiene un gran impacto!

La primera parte del libro es una hoja de ruta para todo lo que necesita aprender para prepararse para el nuevo y mejorado JavaScript que escribirá y explorará en los próximos años.

La última parte del libro dirige la atención a echar un vistazo brevemente a las cosas que probablemente podamos esperar ver en el futuro cercano de JavaScript. La realización más importante aquí es que, después de ES6, JS probablemente evolucionará característica por característica en lugar de versión por versión, lo que significa que podemos esperar ver estas cosas en el futuro cercano mucho antes de lo que imaginas.

El futuro de JavaScript es brillante. ¿No es hora de que empecemos a aprenderlo?

## Review

La serie *YDKJS* está dedicada a la propuesta de que todos los desarrolladores de JS pueden y deben aprender todas las partes de este gran lenguaje. La opinión de ninguna persona, los supuestos del marco y la fecha límite de ningún proyecto deberían ser la excusa de por qué nunca aprende y entiende profundamente JavaScript.

Tomamos cada área importante de enfoque en el lenguaje y dedicamos un libro corto pero muy denso para explorar completamente todas las partes del mismo que tal vez pensaste que sabías pero que probablemente no sabías completamente.

"You Don't Know JS" no es una crítica o un insulto. Es un hecho que todos nosotros, incluido yo mismo, debemos aceptar. Aprender JavaScript no es un objetivo final sino un proceso. Todavía no conocemos JavaScript. Pero lo haremos!
