[0]:http://sadasant.com/ "Daniel Rodríguez"
[1]:http://playground.magicrising.de/2008/03/performance-comparison-between-html-svg-and-canvas/ "Comparación de velocidades entre HTML, SVG y canvas"
[2]:http://www.whatwg.org/specs/web-apps/current-work/multipage/the-canvas-element.html#the-canvas-element "Especificación del elemento canvas"
[3]:http://www.khronos.org/registry/webgl/specs/latest/ "Especificación 3D del objeto canvas"
[4]:http://javascript.about.com/library/blmousepos.htm "Explicación en inglés para la detección del puntero con javascript sin importar el navegador"
[4]:http://jsbin.com/ojehat/ "Lo que el puntero nos dice"
[4e]:http://jsbin.com/ojehat/edit#javascript,html,live "Editar: Lo que el puntero nos dice"
[5]:http://jsbin.com/enagiz/ "Un cuadrado rojo en un canvas con borde rojo"
[5e]:http://jsbin.com/enagiz/edit#javascript,html,live "Editar: Un cuadrado rojo en un canvas con borde rojo"
[6]:http://jsbin.com/enagiz/3/ "Un cuadrado rojo persiguiendo al puntero en un canvas de borde rojo"
[6e]:http://jsbin.com/enagiz/3/edit#javascript,html,live "Editar: Un cuadrado rojo persiguiendo al puntero en un canvas de borde rojo"
[7]:http://jsbin.com/enagiz/4/ "El rectángulo volador"
[7e]:http://jsbin.com/enagiz/4/edit#javascript,html,live "Editar: El rectángulo volador"
[8]:http://www.whatwg.org/specs/web-apps/current-work/multipage/the-canvas-element.html#the-canvas-state "Especificación del elemento canvas: Estados (en ingles)"
[9]:http://www.disfrutalasmatematicas.com/geometria/radianes.html "Más información sobre ángulos radianes"
[10]:http://jsbin.com/opomes/2/ "El círculo volador"
[10e]:http://jsbin.com/opomes/2/edit "Editar: El círculo volador"
[11]:https://developer.mozilla.org/en/html/canvas "Canvas en la Red de Documentos de Mozilla"

Por @[Sadasant][0].

Muchos habrán leído sobre las capacidades que *HTML5* nos trae con su etiqueta *canvas*, nos permite dibujar, editar y animar imágenes dentro del navegador; aunque sigue teniendo [limitaciones de velocidad][1], los motores *JavaScript* y los procesadores actuales están poco a poco avanzando, lo que garantiza un futuro brillante. Canvas posee sin lugar a dudas una de las funcionalidades más útiles de la programación web: hacer imágenes interactivas atentas a las acciones del usuario.

A continuación veremos un ejemplo de cómo hacer un rectángulo que cambie su forma y posición según la posición del puntero. La herramienta que utilizaremos será [jsbin.com](https://github.com/remy/jsbin) creada por [Remy Sharp](https://twitter.com/#!/REM), se trata de un editor de textos en línea para hacer pruebas con *JavaScript*, *HTML* y *CSS* que además tiene incorporado un control de versiones, por lo que podrán editar el código sin afectar el que usaremos en el tutorial.

## Canvas se come con... ##

Tal como nos indica la [especificación del elemento canvas][2], la etiqueta canvas de HTML posee solo dos atributos, ancho (width) y alto (height). De no especificarse el alto y el ancho, canvas toma un tamaño por defecto de 300x150 píxeles.

    <!-- Sintaxis de la etiqueta canvas -->
    <canvas id="avatar" width="301" height="301"></canvas>

Una vez tenemos la etiqueta, el siguiente paso es inicializar el canvas con JavaScript, para esto asignamos el elemento a una variable y habilitamos el contexto en dos dimensiones con el método **getContext**, de la siguiente manera:

    var canvas = document.getElementById("canvas"),
        context = canvas.getContext("2d");
    //  Canvas listo para trabajar

**getContext** retorna un objeto que nos permitirá interactuar con el API para dibujar sobre el *canvas*. A este método le podemos pasar tanto la cadena de caracteres “*2d*”, como la cadena "*webgl*" (con “3d” también sirve), esta última nos permite trabajar con el [API para renderización 3D][3] que actualmente es posible utilizar en la mayoría de los navegadores actualizados.


## Detectando al puntero ##

Antes de pensar qué colocaremos dentro del canvas, obtengamos la posición de puntero. Lo primero que debemos hacer es definir una variable, en este caso utilizaremos una variable global **mouse** que tendrá dos variables internas: "**x**" para guardar el estado de la distancia entre el puntero y el extremo izquierdo del navegador, y "**y**" para guardar la distancia entre el puntero y el tope del navegador.

    var mouse = {
        x: 0,
        y: 0
    };

Es importante entender que JavaScript utiliza como posición inicial (0,0) la esquina superior izquierda de todo objeto/marco/ventana-del-navegador.

Entendido esto, pasamos a inicializar el estado **onmousemove** (almoverseelmouse) dentro del objeto **document** con una función. Al estar inicializado, los navegadores modernos tratarán de enviarle un objeto que tendrá guardada la posición horizontal del puntero en una variable **pageX** y la posición vertical del puntero en una variable **pageY**.

    document.onmousemove = function (e) {
        mouse.x = e.pageX || null;
        mouse.y = e.pageY || null;
    };

Para que podamos obtener la posición sin importar el navegador, el código [aquí explicado][4] es el siguiente:

    document.onmousemove = function (e) {
        var X = (document.all && event.clientX)? event.clientX +
            (document.documentElement.scrollLeft || document.body.scrollLeft) :
            (e.pageX)? e.pageX : null;
        var Y = (document.all && event.clientY)? event.clientY +
            (document.documentElement.scrollTop || document.body.scrollTop) :
            (e.pageY)? e.pageY : null;
        mouse.x = X;
        mouse.y = Y;
    };
**Ejemplo**: [Ver][4], [editar][4e].

Con un poco de atención, podemos ver que antes de finalizar la función del **document.onmousemove** le asignamos los valores de la posición horizontal y vertical al objeto **mouse** que antes inicializamos.


# El rectángulo volador #

Para dibujar un rectángulo con canvas utilizaremos el método **fillStyle** que posee el objeto **context** previamente definido para escoger un color con el que dibujaremos nuestro rectángulo; luego de esto utilizaremos el método **fillRect** del **context**, que recibe como parámetros la posición en X, la posición en Y, el ancho y el alto, en ese orden:

     context.fillStyle = "#FF0000";
     context.fillRect(50, 50, 50, 50);
**Ejemplo**: [Ver][5], [editar][5e].

Para hacer que este se altere con la posición del puntero, basta con enviarle esos datos a **fillRect**, sin embargo, para que se perciba el cambio debemos limpiar el **canvas** y volver a dibujar el rectángulo según la ubicación del puntero. Hay varias maneras de limpiar el **canvas**, el método más sencillo es reiniciar el ancho (width) del canvas, igualándolo consigo mismo mismo. Ordenando un poco las ideas, primero definiremos un objeto literal **rect** que contendrá una función **move** que nos permitirá animar al rectángulo, a esta función la llamaremos eternamente en un intervalo de 35 mili-segundos, de la siguiente manera:

    var rect = {
        move: function () {
            canvas.width = canvas.width;
            context.fillStyle = "#FF0000";
            context.fillRect(mouse.x, mouse.y, 5, 5);
        }
    };
    setInterval(rect.move,35);
**Ejemplo**: [Ver][6], [editar][6e].

Para hacer que el rectángulo se retrase, guardaremos su posición en una variable **pos** dentro del objeto literal **rect** que se irá escribiendo a medida que se vaya ejecutando el intervalo de **rect.move**; luego, guardaremos la diferencia entre la posición del rectángulo y la posición del puntero en las variables **difx** para la diferencia horizontal y **dify** para la diferencia vertical; al aumentar la posición del rectángulo con una fracción de esa diferencia haremos que su desplazamiento se retrase, además, si utilizamos el valor absoluto de esa diferencia mas un valor mínimo (en este caso de 10) podemos modificar proporcionalmente el espesor del rectángulo.

    var rect = {
        pos: {
            x: canvas.width - 5,
            y: canvas.height - 5
          },
        move: function () {
            canvas.width = canvas.width;
            var difx = (mouse.x - rect.pos.x) * 0.25,
                dify = (mouse.y - rect.pos.y) * 0.25;
            rect.pos.x += difx;
            rect.pos.y += dify;
            difx = 10 + Math.abs(difx);
            dify = 10 + Math.abs(dify);
            context.fillStyle = "#FF0000";
            context.fillRect(rect.pos.x - 5, rect.pos.y - 5, difx, dify);
        }
    };
**Ejemplo**: [Ver][7], [editar][7e].

Así conseguimos hacer, de manera sencilla, que el canvas esté al tanto de las acciones del usuario, en este caso específicamente del puntero. 

En un ejemplo un poco más avanzado, podríamos limpiar el *canvas* pintando toda la pantalla con un rectángulo del tamaño del *canvas*, además hacer que el color que usamos sea ligeramente transparente:

      context.save();
        context.fillStyle = "rgba(240, 240, 240, 0.3)"; // el 0.3 indica la transparencia del color RGB
        context.fillRect(0, 0, can.width, can.height);
      context.restore();

Los métodos **save** y **restore** del *contexto* se utilizan para añadir y restaurar los estados del canvas, los estados son el entorno en donde se dibujarán las figuras, para más información pueden  leer [este documento][8].

Además, podemos hacer en vez de un rectángulo, un círculo. Esto se logra utilizando los métodos del contexto **beginPath** para iniciar un patrón distinto a un rectángulo, **arc** para dibujar un patrón con un ángulo de 2π [radianes][9], cerramos el patrón con **closePath** y lo llenamos con **fill**, de esta manera:

      context.save();
          context.translate(this.x,this.y); // posición del punto inicial de dibujo
          context.fillStyle = "#FF0000"; // color de relleno
          context.beginPath(); // iniciamos el patrón
              context.arc(0, 0, this.r, 0, Math.PI * 2); // dibujamos un arco circular
          context.closePath(); // cerramos el patrón
          context.fill(); // llenamos el patrón con el color de relleno
      context.restore();

El ejemplo de un círculo siguiendo al puntero  con cierto efecto de degradación lo pueden ver aquí: [Ver][10], [editar][10e]. Para ver más ejemplos y tutoriales, les recomiendo [la sección de canvas en los documentos de Mozilla][11].

Gracias por su tiempo, espero les haya sido útil este tutorial, sus comentarios son bienvenidos.

