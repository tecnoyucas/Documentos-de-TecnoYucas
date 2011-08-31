[0]:http://sadasant.com/ "Daniel Rodríguez"
[1]:https://secure.wikimedia.org/wikipedia/es/wiki/JavaScript "JavaScript en Wikipedia"
[2]:https://secure.wikimedia.org/wikipedia/es/wiki/Web_2.0 "Web 2.0 en Wikipedia"
[3]:http://nodejs.com/ "Sitio oficial de node.js"
[4]:http://yucazos.tumblr.com/post/9464854469/sadasant-persiguiendo-al-puntero-con-canvas-html5 "Persiguiendo al puntero con canvas de HTML5"
[5]:http://www.openjs.com/tutorials/basic_tutorial/index.php "ABC of JavaScript : An Interactive JavaScript Tutorial"
[6]:http://jsbin.com/usetel/4 "Objetos literales con JavaScript, ver ejemplo"
[6e]:http://jsbin.com/usetel/4/edit "Objetos literales con JavaScript, editar ejemplo"
[7]:https://secure.wikimedia.org/wikipedia/en/wiki/Douglas_Crockford "Wikipedia en inglés: Douglas Crockford."
[8]:http://www.ecma-international.org/publications/standards/Ecma-262.htm "Especificación ECMAscript para el año 1999"
[9]:https://secure.wikimedia.org/wikipedia/es/wiki/Brendan_Eich "Wikipedia: Brendan Eich"
[10]:https://www.mozilla.org/ "Sitio oficial del proyecto Mozilla"
[11]:https://secure.wikimedia.org/wikipedia/en/wiki/ECMAScript "Wikipedia: ECMAScript"
[12]:https://secure.wikimedia.org/wikipedia/es/wiki/Java_%28lenguaje_de_programaci%C3%B3n%29 "Wikipedia: JAVA"
[13]:http://json.org/example.html "Ejemplos de JSON en ingles"
[14]:http://www.w3.org/TR/XMLHttpRequest/ "Especificación del objeto XMLHttpRequest"
[15]:http://jsbin.com/awonuj/2 "Ejemplo de AJAX con JSON"
[15e]:http://jsbin.com/awonuj/2/edit "Editar: Ejemplo de AJAX con JSON"
[16]:http://jsbin.com/ixihud/5 "JSON que usé con el ejemplo de AJAX"
[16e]:http://jsbin.com/ixihud/5/edit "Editar: JSON que usé con el ejemplo de AJAX"
[17]:http://api.jquery.com/jQuery.getJSON/ "JSON en jQuery"
[18]:http://www.prototypejs.org/learn/json "JSON en Prototype"
[19]:http://mootools.net/docs/core/Utilities/JSON "JSON en MooTools"
[20]:https://closure-library.googlecode.com/svn/docs/closure_goog_json_json.js.html "Código libre JavaScript para interpretar JSON dentro de la estructura de Closure, de Google"
[21]:http://sadasant.com/tweet/ "A minimalist-to-hurt twitter client."
[22]:https://dev.twitter.com/docs/anywhere/welcome "API Anywhere de Twitter"
[23]:https://dev.twitter.com/docs/api/1/get/search "API para buscar tuits públicos en Twitter"
[24]:https://dev.twitter.com/docs/auth/oauth "Twitter's OAuth process"
[25]:https://github.com/themattharris/tmhOAuth "TMHOAuth: Librería en PHP para Twitter"
[26]:http://tuitpix.com/ "Tuitpix.com ~ Herramienta HTML5 para crear avatares Pixel Art"
[27]:http://www.tumblr.com/docs/es/api "API de Tumblr en ingles"
[28]:https://secure.wikimedia.org/wikipedia/en/wiki/JSONP "JSONP en Wikipedia (ingles)"
[29]:http://www.w3.org/TR/XMLHttpRequest/#states "Estados de la especificación del objeto XMLHttpRequest"

Por @[Sadasant][0].

El lenguaje de programación *[JavaScript][1]* fue creado por [Brendan Eich][9] en 1995 (Netscape, ahora [Mozilla][10]) a partir del lenguaje [ECMAScript][11],  su finalidad era competir con [JAVA][12] como lenguaje de interfaces de usuarios para la *web*. Hoy en día, JavaScript es el "aire de internet", se convirtió en estándar entre todos los navegadores y sus cualidades han permitido a la web convertirse en la "[*web 2.0*][2]". Adicionalmente, todos los computadores y dispositivos móviles con conexión a internet lo soportan y del lado del servidor se está haciendo sentir a través de proyectos como *[node.js][3]*.

Hace unos días publiqué una [práctica con el elemento canvas de HTML5][4], esta vez les mostraré una demostración de *JSON* y *AJAX*, dos tecnologías que juntas facilitan la comunicación asíncrona entre el cliente y el servidor y le brindan a los sitios más actualizados su dinamismo.

Para los que quieren aprender *JavaScript*, mi tutorial favorito se encuentra [aquí][5] (está en Inglés), dentro de poco le haré una adaptación al español, ¡paciencia! :).

### 1. JSON ###

Los objetos literales son uno de los tipos de variables más prácticos de *javascript*, similares a las que en otros lenguajes llaman "listas", "diccionarios" o "arreglos asociativos", pueden guardar de manera organizada cualquier otra variable, función u objeto. La sintaxis es la siguiente:

    var literal = {
        
        "Un arreglo": [ 1, "dos", 3 ],
        
        "funcion": function (texto) {
            alert(texto);
        }

    };
    
    literal.funcion(literal["Un arreglo"][2]);
    //alertará el número 3
**Ejemplo**: [Ver][6], [editar][6e].

Un pequeño ejemplo de un objeto literal sería el de arriba; la variable de nombre **literal** contiene "Un arreglo" con tres elementos y una función de nombre "funcion" que ejecutará un **alert()** con el primer parámetro que se le envíe. Luego de definir sus componentes, procedemos a ejecutar la función interna, llamándola directamente con un punto después del nombre del objeto ("literal.funcion()"); a esa función le pasamos como parámetro la variable ubicada en la **tercera posición** (en programación se cuenta desde el cero) del arreglo "Un arreglo", lo que hará que la **funcion** ejecute un **alert(3)** y nos lance en pantalla el número 3.

El arreglo, al tener un identificador con un espacio de por medio, no puede ser llamado sólo con un punto, por lo que se coloca la cadena con el nombre exacto entre corchetes ("[]"). Los identificadores de las variables internas de estos objetos, en el caso de no tener espacios, pueden ser colocados sin el uso de comillas dentro del objeto literal.

**¿A qué viene todo esto?**

En el 2002 [Douglas Crockford][7] publicó el sitio web <http://json.org> como resultado de sus prácticas exitosas con una perspectiva innovadora del [estándar de objetos literales en JavaScript][8]; se trataba de usarlos como un formato de texto plano, ligero y entendible a simple vista, para el intercambio de datos entre distintos sistemas computacionales.

*JSON* soporta todos los tipos de variables de JavaScript menos los tipo Fechas (Date), Error, Matemáticos (Math), Expresiones Regulares, Funciones y Objetos (frecuentemente inicializados con "new"). JSON requiere que todos los elementos de los objetos internos (diferenciados por el uso de llaves "{}") tengan identificadores encerrados entre comillas dobles ( "identificador" ), además no se puede terminar un arreglo u objeto literal con componentes inconclusos (con una coma antes del último corchete o llave). Ejemplo de JSON:

    {
        "Autor": "Daniel R. (sadasant.com)",
        "null": null,
        "Un arreglo": [
            "Lápiz", "papel", "alerta",
            1, 2, 3
        ],
        "Un objeto literal": {
            "Con vida": [ "humano", "gato", "perro" ],
            "Metálico": [ "robot", "tostadora" ],
            "Comida":   [ "tortas", "frutas" ]
        }
    }


JSON es texto plano, por lo que para obtener sus datos primero debe ser transformado en variables entendibles por JavaScript, por fortuna, debido a su relación tan estrecha, basta con ejecutar un "eval(**json**)" para que se transforme en un objeto al que se le puedan extraer los datos.

    var p = eval("(" + cadenaDelJSON + ")");

La variable donde esté guardada la cadena del JSON debe *evaluarse* entre paréntesis para evitar ambigüedades con la sintaxis de JavaScript. Es importante comentar que, para prevenir que código malicioso se ejecute, es recomendable evitar el **eval** y utilizar librerías como [jQuery][17], [Prototype][18] y [MooTools][19], o también, librerías dedicadas como esta: [enlace][20].

Aquí pueden ver mas ejemplos de JSON y comparaciones con la sintaxis XML: [enlace][13].

### 2. AJAX ###

*AJAX*, acrónimo en ingles de "JavaScript y XML asíncronos", es una técnica de desarrollo web para descargar contenido en ubicaciones externas a la página actual sin afectar su funcionamiento o recargarla, lo que permite hacer que la información vaya cargando a medida que el usuario explora la interfaz.

El objeto que se utiliza para estas operaciones se llama ***XMLHttpRequest***, la especificación la pueden ver [aquí][14].


    var ajax = new XMLHttpRequest();
    ajax.open("GET", "http://jsbin.com/ixihud/5/js", true);
    ajax.onreadystatechange = function () {
        if ( ajax.readyState == 4 && ajax.status == 200 ) {
            alert(ajax.responseText); // DESCARGAMOS EL TEXTO
        }
    };
    ajax.send(null);

AJAX es muy usado para descargar archivos de texto en formato JSON, en el ejemplo anterior suponemos que tenemos un JSON ubicado en esta URL: <http://jsbin.com/ixihud/5/js>, para obtenerlo definimos la variable ajax como un nuevo objeto **XMLHttpRequest**, luego hacemos que abra un pedido con los parámetros "GET", la URL y **verdadero** (para que llame al contenido de manera asíncrona). Además, al objeto definido en **ajax** le asignaremos una función llamada **onreadystatechange** que, en el caso de que haya concluido exitosamente (readyState == 4 y status == 200, ver mas [aquí][29]), nos permitirá manejar la respuesta, ubicada en "ajax.responseText". Finalmente enviamos el pedido sin ningún dato adicional con "**ajax.send(null)**".

La web <http://jsbin.com/> tiene una implementación de JSON que nos permitirá ejecutar **JSON.parse** para obtener los datos:

        if ( ajax.readyState == 4 && ajax.status == 200 ) {
            JSON.parse(ajax.responseText);
        }

Para poder ver el contenido del JSON, podemos recorrerlo con un ciclo **for** y extraer su contenido, abajo podrán ver un ejemplo, primero creo una variable **select** que buscaremos llenar con los componentes internos del JSON, para lo cual utilizamos un ciclo "**for (var i in json)**", donde la "**i**" pasará a tener cada uno de los identificadores del **json**, por lo que podremos llenar la lista con *opciones* de a cuerdo a estos identificadores:

    // listbox
    var select = ["<select onchange='example.change();'>","","</select>"];
    for (var i in json) {
      select[1]+= "<option>"+i+"</option>";
    }
    p.innerHTML = select.join("");

A la lista le colocamos dentro del atributo "**onchange**" un llamado a la función **example.change()**, lo que nos permitirá ,a penas el usuario cambie de selección, obtener la identificación del elemento seleccionado y con ella extraer los datos del JSON:

    var example = {
        // . . .
        change: function(){
            var s = document.getElementsByTagName("select")[0], // obtenemos el select
                v = s.options[s.selectedIndex].value; // obtenemos el valor de la opción seleccionada
            v = this.json[v]; // extraemos el valor del JSON según la opción del select
        }
    }

Un ejemplo con todo lo que les he mostrado hasta este punto lo pueden conseguir aquí: [Ver][15], [editar][15e]. En ese ejemplo utilicé este JSON: [Ver][16], [editar][16e].

### 3. JSON, AJAX y las Redes Sociales ###

JSON en la actualidad es ampliamente utilizado por servicios en la web, todas las redes sociales más usadas lo utilizan. En ese aspecto, Twitter es la que más he utilizado; en mi sitio web tengo un [pseudo-cliente minimalista de Twitter][21] en el que hago uso del [API Anywhere de Twitter][22] mas el [API de búsquedas públicas][23] que me permite encontrar las menciones y las publicaciones del usuario. En ese cliente pueden ver las siguientes líneas de código, con las cuales hago las búsquedas, primero defino la URL, luego configuro el ajax de jQuery, defino que serán datos **jsonp** (más información sibre JSONP [aquí][28]), y le indico que cuando el AJAX sea exitoso ejecute la función "**sdsnt.jsonp**":

        search_string: "http://search.twitter.com/search.json?q=to%3Auser%20OR%20%40user&rpp=5",
        search: function() {
            $.ajax({
                url: sdsnt.search_string.replace(/user/g,sdsnt.user),
                dataType: "jsonp",
                jsonpCallback: "sdsnt.jsonp"
            });
        },

Twitter permite utilizar JSON con sus datos privados, una vez autenticamos a los usuarios con el [api OAuth][24], así podríamos obtener menciones y mensajes directos siempre y cuando el usuario acepte el uso de nuestra aplicación. Mis pruebas con OAuth se resumen a utilizar la librería para PHP llamada "*[TMHOAuth][25]*" asegurarme de que el usuario esté conectado y, si él quiere, mandar un *tweet* y publicar una imagen en su perfil, eso forma parte del funcionamiento de una de mis prácticas: [Tuitpix.com][26].

Otra de las redes sociales interesantes en este aspecto es Tumblr, el [Api de Tumblr][27] tiene un modo práctico de utilizar el JSON, ya que al descargarlo viene incluido con el JavaScript que lo interpreta, así que con las siguientes líneas podemos obtener nuestras últimas publicaciones sin más complicaciones:  

    <script type="text/javascript" src="http://(you).tumblr.com/api/read/json"></script>
    // La Variable "tumblr_api_read" está cargada.
    var url_del_ultimo_post = tumblr_api_read[1][0]['url'];

Cualquier otra duda que tengan al respecto, comenten este artículo o contáctenme en alguna red social :) espero les haya sido de utilidad.
