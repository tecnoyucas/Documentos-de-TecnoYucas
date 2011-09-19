[0]: http://sadasant.com/ "sadasant.com"
[0l]: http://eloquentjavascript.net/contents.html "Eloquent JavaScript: A Modern Introduction to Programming"
[1]: https://secure.wikimedia.org/wikipedia/es/wiki/JavaScript "Wikipedia: JavaScript"
[2]: https://secure.wikimedia.org/wikipedia/es/wiki/Lenguaje_de_programaci%C3%B3n "Wikipedia: Lenguajes de Programación"
[3]: https://secure.wikimedia.org/wikipedia/es/wiki/L%C3%B3gica "Wikipedia: Lógica"
[4]: https://secure.wikimedia.org/wikipedia/es/wiki/Java_%28lenguaje_de_programaci%C3%B3n%29 "Wikipedia: Java"
[4]: https://secure.wikimedia.org/wikipedia/es/wiki/Fundaci%C3%B3n_Mozilla#Historia "Wikipedia: Historia de Mozilla"
[5]: https://secure.wikimedia.org/wikipedia/en/wiki/Brendan_Eich "Brendan Eich, actual director de tecnología en Mozilla"
[6]: https://secure.wikimedia.org/wikipedia/en/wiki/Dynamic_language "Wikipedia: Lenguajes Dinámicos"
[7]: http://www.ecma-international.org/publications/standards/Ecma-262.htm "Especificación del lenguaje ECMAScript"
[8]: https://secure.wikimedia.org/wikipedia/en/wiki/Actionscript "Wikipedia: ActionScript"
[9]: https://secure.wikimedia.org/wikipedia/en/wiki/First-class_function "Wikipedia: First-class functions"
[10]: https://developer.mozilla.org/en/JavaScript/Guide/Values%2c_Variables%2c_and_Literals "MDN: Javascript, Values, Variables, and Literals"

por [Daniel R][0].

Este documento es el primero de una serie de tutoriales dedicados a proveer una guía práctica para entender y hacer uso del lenguaje de programación *JavaScript*. Está redactado con la intención de que entuciastas del código o programadores avanzados puedan conocer más sobre este lenguaje. Si desean empezar desde cero en el mundo de la programación web, les recomiendo [este libro en línea][0l] (está en inglés).

En esta "primera edición" me enfocaré a contar un resumen de la historia del lenguaje, sus valores, condicionales, ciclos y el alcance de las variables. En las siguientes semanas cubriré la interacción con el el contenido de los sitios web, el uso y límites de las librerías más comunes, los principios básicos de la programación orientada a objetos y mezclaré todo con las capacidades del paradigma de programación funcional que tiene *JavaScript*.

Antes de este tutorial les comento que he hecho otros relacionados, si tienen interés sobre los puntos que tocan no duden en revisarlos:

* [Siguiendo al puntero con el canvas de HTML5](http://yucazos.tumblr.com/post/9464854469/sadasant-persiguiendo-al-puntero-con-canvas-html5)
* [JSON y AJAX básicos con JavaScript](http://yucazos.tumblr.com/post/9632056853/json-y-ajax-con-javascript)
* [Prácticas con RaphaëlJS](http://sadasant.com/d/b/#RaphaelJS)

A medida de que vayamos avanzando, haré referencia a otras fuentes que sirvieron de inspiración y bases referenciales para realizar esta publicación, sean curiosos y busquen en otros lugares, hay personas con muchísma más experiencia que yo tanto desde el punto de vista técnico como desde el punto de vista pedagógico. Aquí tienen una lista de otros tutoriales relacionados que he conseguido:

* Mozilla Document Network - JavaScript: [Inglés](https://developer.mozilla.org/en/JavaScript). [Español](https://developer.mozilla.org/es/JavaScript).
* JavaScript in ten minutes: [Inglés](http://javascript.infogami.com/Javascript_in_Ten_Minutes)
* JavaScript Garden: [Inglés](http://bonsaiden.github.com/JavaScript-Garden/)
* ABC of JavaScript ~ An Interactive JavaScript Tutorial: [Inglés](http://www.openjs.com/tutorials/basic_tutorial/index.php)
* *Manden sus recomendaciones :D*

Finalmente, a continuación les dejaré una lista de sitios donde pueden hacer pruebas de javascript en línea mientras leen el tutorial:

* <http://jsbin.com>
* <http://jsfiddle.net>
* <http://jsdo.it>

### ¿Qué es JavaScript? ###

*Tan resumido que duele*

*[JavaScript][1]* es un [lenguaje de programación][2] pensado para hacer dinámicos a los sitios web. Los lenguajes de programación son lenguajes artificiales que expresan [reglas lógicas][3] que le dirán a su intérprete qué acciones debe realizar para resolver problemas. En el caso de JavaScript dentro de los sitios web, su intérprete es el navegador (Firefox, Chrome, Opera, Safari, MSIE), el cual entiende el funcionamiento de las órdenes que recibe para hacer que la navegación por internet sea más interactiva, y regula su ejecución para evitar posibles problemas de seguridad.

*Un poco de historia...* [Fuente](http://ask.metafilter.com/195482/Lets-assume-that-I-am-the-stupidest-person-that-ever-lived-Explain-to-me-what-JavaScript-is-what-it-does-and-how-a-moron-would-go-about-learning-it#2813956)

Es importante aclarar que **[JavaScript][1]** es un lenguaje completamente distinto a **[Java][4]**. Antes de que [AOL comprara Netscape y surgiera Mozilla][5], la empresa SUN ya había inventado Java y quería que el navegador más usado del momento (Netscape) lo interpretara para así incentivar el desarrollo de aplicaciones web utilizando este lenguaje. Netscape no estaba del todo conforme, así que luego de aceptar la propuesta de Java, le preguntó a SUN si podía darle el nombre de "JavaScript” a un lenguaje que estaría también destinado a desarrollar aplicaciones web, pero de una manera más sencilla y práctica. SUN aceptó sin darle mucha importancia y Netscape le dijo a [uno de sus programadores][5] que hiciera en 10 días un lenguaje llamado *JavaScript* que fuese de algún modo similar a Java. Este terminó siendo un lenguaje complétamente distinto, y a pesar de que su recibimiento no fue completamente grato, años después sería quien ganaría la batalla por la web y se convertiría en uno de los lenguajes más usados del mundo.

En algún punto de la historia, Netscape y la asociación europea para la información estandarizada ECMA colaboraron para hacer la [especificación ECMAScript][7] (que ahora también es una ISO llamada ISO-16262), desde donde surge el JavaScript que hoy día conocemos así como otros lenguajes, como el [ActionScript][8].

*¿Qué lo hace tan distinto?*

La sintaxis básica de JavaScript se parece en cierta manera a la de *Java* (y a la de *C*), en cuanto a como funcionan los condicionales (*if*, *else*), los ciclos (*while*, *for*) y otros bloques (*try*, *catch*); sin embargo, JavaScript es un lenguaje [dinámico][6] (que no necesita ser compilado), donde *todo es un objeto* y los objetos están basados en *prototipos* (más adelante iremos con detalles), además no es necesario definir el tipo de variable y sus funciones y objetos son de [primer orden][9] (que pueden ser pasados como variables, asignados a variables y/o retornados, entre otras cosas, luego entramos en detalles -_- ).

### Valores, Variables y Literales ###

Tal como podemos conseguir en la [red de documentos de Mozilla][10], Los valores en JavaScript pueden ser números (enteros, decimales), cadenas de texto (con ninguno, uno o más caracteres, `"de esta manera"`), lógicos (booleanos, verdadero y falso), `null` que denota un valor nulo, y `undefined` que denota un valor indefinido. Además existen objetos y funciones, siendo los objetos contenedores de valores y las funciones conjuntos de procedimientos para el funcionamiento del código.

En ese orden de ideas, el primer ejemplo que tenemos es con números, a continuación pueden ver como declaro la variable `number`, le asigno un cero y luego cambio su valor por 1.5.

    /* Tipo: 'number' */
    var number = 0; // asignamos un cero
    number = 1.5; // reemplazamos el cero por un 1.5

En el segundo ejemplo asigné varias cadenas de caracteres, la primera la declaramos con `var `, luego cambiamos su valor por `'otra cadena'` y finalmente por un texto dividido en varias líneas por su longitud.

    /* Tipo: 'string' */
    var texto = "Cadena de caracteres";
    texto = 'otra cadena';
    texto = "Texto muy largo,\
             así lo podemos separar"+ // aquí concatenamos
            "en varias líneas.";

Un punto interesante del ejemplo de arriba es la separación de líneas para textos largos, si se desea hacer dentro de la misma cadena de texto se, debe terminar cada línea con un *backslash* `\`. Otra manera de hacerlo es concatenando una cadena con otra, para esto podemos utilizar el símbolo de suma `+`, aunque [hay muchas formas de hacerlo](http://stackoverflow.com/questions/112158/javascript-string-concatenation) y [algunas son mejores que otras](http://www.sitepen.com/blog/2008/05/09/string-performance-an-analysis/). Más adelante hablaremos en detalle sobre el operador de suma `+` y otros.
 
Este tipo de separación de líneas simplemente se utilizan para mantener ordenado el código. Para insertar líneas nuevas se debe añadir "`\n`" o isertar la etiqueta *break* `</br>`. En  [este enlace](https://developer.mozilla.org/en/JavaScript/Guide/Values%2c_Variables%2c_and_Literals#String_Literals) pueden encontrar una lista de todos los caracteres especiales dentro de las cadenas de texto en JavaScript (Buscar: "JavaScript special characters").

El siguiente ejemplo es sobre los valores booleanos, en JavaScript verdadero se escribe `true` y falso `false`, ambas deben ser en minúsculas.

    /* Tipo : 'boolean' */
    var bool = false; // bool es falso
    bool = true; // bool es verdadero

Para que un valor sea nulo debe declararse explícitamente como nulo, aunque otros valores pueden ser válidos como nulos si se evalúan con dos iguales (`==`). Por otra parte, los valores indefinidos no han sido declarados o no existen en el código en ejecución. Los valores nulos e indefinidos están ilustrados en el siguiente ejemplo:

    /* Tipo : 'null' */
    var nulo = null;

    /* Tipo : 'undefined' */
    var indefinido;

Además de ese tipo de variables, existen otras que permiten organizar o agrupar conjuntos de variables, como por ejemplo: los arreglos.

Los arreglos se pueden instanciar sin necesidad de llamar al objeto "`Array`" al utilizar un par de corchetes "`[]`", los cuales tendrán una posición por cada valor o variable que tengan dentro, separados por comas "`,`", de esta manera:

    /* Llamando al objeto Array */
    var arreglo = new Array("uno",2,3);
    
    /* Arreglos literales */
    arreglo = ["uno",2,3];
    
    /* accediendo a los valores del arreglo */
    alert(arreglo[0]); // alertará "uno"
    
    /* Arreglos con arreglos dentro */
    arreglo = [["uno","dos"],[1,2,3]];

Para encontrar valores dentro de arreglos se utilizan también corchetes "`[]`", dentro de los cuales se debe colocar la posición del valor que se desea encontrar.

Finalmente existen los objetos literales, que proveen una forma más organizada y funcional de almacenar otros valores. En otros lenguajes suelen llamarlos “listas”, “diccionarios” o “arreglos asociativos”. La sintaxis es la siguiente:

    /* Objeto literal */
    var O = { a: "uno", b: "dos", c: "tres"};
    
    /* Accediendo a sus valores */
    alert(O.a); // alertará: uno
    alert(O.b); // alertará: dos
    alert(O["c"]); // alertará: tres

Para obtener valores dentro de los objetos literales se pueden buscar diréctamente utilizando un punto seguido del nombre del valor "`objetoLiteral.nombreDelValor`" (solo si el nombre no tiene espacios), o con el uso de corchetes: "`objetoLiteral["Nombre del valor"]`".

Tanto los arreglos literales como los objetos literales pueden contener *lo que sea*, incluyendo otros objetos y funciones.

### Condicionales ###  

Con variables no es suficiente, hace falta una estructura lógica para poder interactuar con ellas. Los condicionales nos permiten separar procesos de ejecución si una afirmación se cumple. Por ejemplo, si declaramos una variable con un valor tres (3), podríamos compararla con otra variable y ejecutar diferentes acciones según sean iguales o distintas, así:

    var tres = 3,
        seis = 6;
        
    if (tres == seis){
        alert("Son iguales");
    } else {
        alert("Son diferentes");
    }

Es posible hacer múltiples comparaciones si utilizamos otro if después del else, de esta manera:

    var tres = 3,
        
    if (tres == 3){
        alert("Es un tres");
    } else
    if (tres == 4){
        alert("Es un cuatro");
    } else {
        alert("No es tres ni es cuatro");
    }

También es posible hacer múltiples comparaciones dentro de un mismo `if`.

    if (tres == 3 || tres == 4) {
        alert("Es un tres o un cuatro");
    }

Otra manera de hacer comparaciones es con `switch`, que extiende una lista de casos posibles con acciones por hacer en caso de que el contenido de la variable que se le pasa entre paréntesis coincida con alguno de los valores en la lista, de esta manera:

    switch(tres){
        case 3:
            alert("Es un tres");
            break; // Separa los casos
        case 4:
            alert("Es un cuatro");
            break;
        default:
            alert("No es tres ni es cuatro");
            break;
    }

En el ejemplo anterior, utilizamos "`break;`" para separar los casos posibles y utilizamos el caso "`default:`" para indicar qué hacer en caso de que no ocurra ninguno de los casos.

Otro modo de hacer condicionales es utilizando los operadores ternarios, básicamente hacen una comparación entre paréntesis y si se cumple ejecutan la primera opción dada, si fallan ejecutan la segunda, la sintaxis es así:

    var a = (tres == 3)? "Es un tres" : "No es un tres";
    
En el ejemplo anterior, la variable "a" contendrá "Es un tres" si es igual a 3, de lo contrario se le asignará "No es un tres".

### Operadores ###  

Antes de seguir es importante entender los operadores de JavaScript, estos nos permitirán asignar valores, cambiar valores y/o compararlos con otros.

Los operadores son símbolos especiales que indican operaciones sencillas entre valores y/o variables, por ejemplo, los operadores aritméticos son los siguientes:

    x + 1; // suma
    x - 1; // resta
    x * 1; // multiplicación
    x / 1; // división

Los operadores más comunes para la asignación de variables son los siguientes:

    x = 1;   // x obtiene el valor 1
    x += 1;  // x aumenta su valor en uno
    x -= 1;  // x disminuye su valor en uno
    x *= 1;  // x multiplica su valor por uno
    x /= 1;  // x divide su valor entre 1
    x++;     // x aumenta su valor en 1
    x--;     // x disminuye su valor en 1

Cuando colocan un operador antes de un igual, están igualando la variable al resultado de utilizar el operador con lo que se encuentra al otro lado de la variable, entonces:

    /* Son lo mismo */
    x += 1;
    x = x + 1;

    /* Son lo mismo */
    x -= 1;
    x = x - 1;

También existen operadores comparativos, los cuales son:

    (x == 1)  // ¿x es igual a 1?
    (x != 1)  // ¿x no es igual a 1?
    (x === 1) // ¿x es igual a 1 y son del mismo tipo de variable?
    (x !== 1) // ¿x no es igual a 1 ni a su tipo de variable?
    (x > 1)   // ¿x es mayor que 1?
    (x < 1)   // ¿x es menor que 1?
    (x >= 1)  // ¿x es mayor o igual a 1?
    (x <= 1)  // ¿x es menor o igual a 1? 

Losparéntesis son necesarios para aislar las operaciones del resto del código, así como para ordenar quienes se ejecutarán primero, por ejemplo: en "`x / y + z`" se dividirían primero "`x / y`" y luego se sumarían con "z", en cambio, si colocamos esa operación así: "`x / ( y + z )`" primero se suman "`y + z`" y luego "x" se divide entre esa suma.

 En [este enlace](https://developer.mozilla.org/es/Gu%C3%ADa_JavaScript_1.5/Expresiones_y_operadores#Operadores) pueden conseguir la lista detallada de los operadores que posee JavaScript.

### Ciclos ###  

El siguiente paso para hacer que el código sea eficiente es mediante el uso de ciclos. Los ciclos evitan que tengamos que re-inicializar todo el programa cada vez que queramos repetir un resultado, o mejor aún, permiten repetir secuencias lógicas con nuevos valores de entrada una cantidad de veces determinada (aunque podrían ser infinitas).

El modo mas intuitivo de hacer ciclos es mediante la expresión `for`, la cual se traduce como "para" y es capaz de evaluar el avance progresivo de asignaciones de valores a una variable determinada, y según ese avance, ejecutará su contenido hasta que se cumpla con una condición dada. Es mejor que vean el ejemplo:

    for ( var i = 1; // declaramos i con valor 0
          i < 11;    // Cuando "i" sea 10 o más, se cerrará el ciclo
          i++        // le suma uno a i cada vez que el ciclo se repite
        )
    { 
        /* abrimos un bloque */

        alert(i); // ejecutamos algo dentro
    }
    
    /* En resumen: */
    for (var i = 1; i < 11; i++ ){ 
        alert(i);
    }

[Ver ejemplo](http://jsbin.com/esepah/edit#preview), [Editar ejemplo](http://jsbin.com/esepah/edit#javascript).

Es usual en los ciclos "`for`" utilizar el operador de asignación "++", que aumenta en uno el contenido de la variable, así mismo, si utilizáramos "--" se restaría en uno, lo que nos permitiría, por ejemplo, empezar en "`i = 10`" e ir restándole uno a "i" hasta que sea cero. Al colocar los *signos dobles* después de la variable hacen que la variable se afecte al terminar el bloque del ciclo, en cambio si, por ejemplo, colocáramos los signos dobles antes de la variable: "`for (var i = 0; i < 11; ++i)`", el bloque del ciclo empezaría con uno en vez de cero.

Otra manera de hacer esto es mediante un "`while`". Los "`while`" (Traducción: mientras) son un proceso "más manual" de hacer ciclos, solo evalúan si un valor es cierto, y si es cierto ejecutan su contenido hasta que no sea cierto, como en el siguiente ejemplo:

    var i = 1;
    while (i < 11) {
        alert(i);
        i += 1;
    }

Acabamos de declarar una variable "i" con valor cero, luego ejecutamos un código que alertará el valor de "i" y le sumará la cantidad de uno "1" mientras la condición del "`while`" fuese cierta. En este caso ocurriría solo si el valor de "i" se mantuviera menor a once. Como estamos haciendo una suma dentro del "`while`", luego de ejecutarse 10 veces, el valor de i sería 11 y el "`while`" dejaría de funcionar.

Si no limitamos los ciclos según sus condicionales, podemos salirnos de ellos utilizando "`break`" para que cancele su funcionamiento o "`continue`" para que siga con la siguiente iteración, de esta manera:

    var i = 1;
    while (true) {
        i += 1;
        if (i == 3) break;
    }

    /* En resumen: */
    for (var i = 1; i < 11; i++ ){ 
        if (i == 3) continue;
        if (i == 5) break;
        alert(i);
        // alert no ocurrirá si: i == 3
        // alert ocurrirá hasta el número 4
    }

Pueden ver que coloqué un "`true`" dentro de la expresión del "`while`", de esta manera el ciclo es infinito, y si no se rompe en algún momento (con "`break`") nuestro computador puede llegar a tener problemas y se puede cerrar el navegador.

### El alcance de las Variables ###  

Ya que entendimos qué tipo de variables hay y algunas maneras básicas de cómo interactuar con ellas, es importante entender cómo funcionan según su entorno. En JavaScript, todo lo que se declara en un entorno se queda en ese entorno y no puede salir de él, por ejemplo, si declaramos una variable fuera de todos los bloques, el entorno que la rodea automáticamente será la página actual y la variable solo podrá se accesible lo que se encuentre en esa ventana. Lo mismo ocurre cuando encerramos una variable en un bloque, las variables encerradas en bloques solo pueden ser accedidas dentro de ese bloque y no desde afuera, por ejemplo, si declaramos una variable dentro de un ciclo, solo puede ser accedida dentro del ciclo y no fuera de él:

    /* Variable externa es leída dentro del ciclo */
    var i = 1;
    while (true) {
        var a = "Variable interna";
        i += 1;
        if (i == 3) break;
    }
    alert(a); // alertará indefinido

El código anterior alerta "`undefined`" porque la variable "a" fue declarada dentro del ciclo, y por ende no puede ser accedida desde afuera, sin embargo dentro del ciclo podemos afectar a variables externas. Entender este detalle nos ayudará a pasar menos dolores de cabeza :)

Hasta aquí llega el tutorial de este fin de semana, ¡Espero les haya servido de utilidad! No se les olvide publicar sus comentarios, si tienen críticas mejor, de ese modo podré corregir mis errores y mejorar mi publicaciones :) 

La semana que viene publicaré un artículo sobre la interacción con los sitios web con ejemplos prácticos e interactivos, estén pendientes.
