## PROCESOS Y RESPUESTAS

### LA TABLA DE RESPUESTAS \(R\)

La tabla de Respuestas \(R\) del menú principal es una forma especial de tabla de Procesos. Una tabla de procesos puede verse como un lenguaje de programación secuencial \(se ejecuta un comando en cada turno\). Las órdenes que se llevan a cabo se llaman "CondAccs" porque se pueden dividir principalmente en dos grupos: condiciones y acciones.

Antes mencionamos que el PARSER de PAW divide las sentencias en frases, las cuales son organizadas entonces en lo que se conoce como SL \(sentencias lógicas\).

En el caso de direcciones como NORTE \(que es una sentencia lógica por sí sola\), PAW usa la tabla de conexiones para descubrir hacia donde se ha de mover el jugador.

ANTES, sin embargo, PAW mira en la tabla de RESPUESTAS para ver si hay alguna entrada en ella que pueda asociar con la SL.

Es muy importante que quede claro el concepto de que cada frase que el jugador teclee y PAW entienda, debe tener su correspondiente entrada en la tabla de Respuestas, excepto por la mayoría de los movimientos, que han sido ya puestos en la tabla de Conexiones.

La parte más importante de una SL es el verbo, que muestra la intención de la frase; la siguiente en importancia es el primer nombre, que muestra el sujeto de la SL, por ejemplo en "coger manzana", coger es el objetivo y manzana es el sujeto.

Si ahora seleccionamos R del menú principal aparecerá el submenú de esa tabla. Tecleando P para mirar la tabla e ignorando de momento cualquier otra entrada, vamos a considerar la entrada que pone:

I \_ INVEN

Las dos palabras \(porque \_ es una palabra\), indican el verbo y el nombre respectivamente. Como es un nombre convertible en verbo \(como vimos en la sección de Vocabulario\) esto significa que si se teclea por sí solo, es decir, si es la única palabra que ha tecleado el jugador en la frase, será tomada como un verbo en la SL. La línea \( \_ \) indica que el nombre no es importante en esta entrada, significaría como el "no palabra" que vimos en la tabla de objetos y palabras.

Lo que esto significa es que si el jugador teclea I sólo, PAW lo equiparará con la primera entrada de la tabla de Respuestas que tenga la I, y ejecutará la orden que se describa al lado de ella. Para ejecutar una sentencia, PAW tiene que ejecutar cada uno de los condacc \(órdenes\) en una lista que ya tiene. Ahora viendo en nuestro ejemplo la palabra I solamente tiene un condacc.

**INVEN:** es una acción \(¡la parte activa de un condacc!\). Y es la parte activa porque se encarga de hacer una lista de los objetos que el jugador esté llevando consigo o tenga puestos encima, en la pantalla. No te preocupes de momento por cómo hacer esto, sólo nos interesa saber que lo hace. Cuando tecleaste I \(o INVENTARIO si lo has puesto como sinónimo\) durante la prueba del juego, fue esta entrada en la tabla de Respuestas la que causó que pasase algo, porque se creó por el PARSER una sentencia lógica de "I \_", que entonces PAW emparejó con la primera entrada en la tabla-respuesta.

INVEN, después de que ha hecho una lista de todos los objetos que lleves, ya le dice automáticamente a PAW que ha hecho algo, y cuando PAW descubre esto, busca en el PARSER otra sentencia lógica, la cual el PARSER ofrece, decodificando las siguientes frases en el INPUT del jugador. PAW entonces coge esta nueva SL y la compara con todas las entradas que hay en la tabla de Respuestas, y así sucesivamente.

Diagrama 4

Este bucle \(loop\) se muestra en el diagrama 4 en forma de una carta de flujo que se puede seguir desde el cuadrado marcado con "comienzo". El bucle es bastante más complejo que lo que el diagrama te pueda parecer y de hecho se da una versión más completa en la guía técnica, pero de momento el diagrama 4 nos servirá.

Te aconsejamos fervientemente que vuelvas a leer los párrafos anteriores y estudies el diagrama, hasta que entiendas cómo PAW trabaja sobre una sentencia lógica antes de funcionar.

Vamos a considerar la segunda entrada de Respuestas:

Hacer I INVEN

Como habrás deducido hábilmente, esta entrada toma en cuenta otra forma de la cual el jugador puede pedir una lista de objetos. Veamos ahora la entrada que pone QUIT \_ \(para hacer esto basta con apretar cualquier tecla excepto BREAK, ESPACIO o N\):

`FIN _     QUIT`

`TURNS`

`END`

Bien, FIN es un verbo en el vocabulario, así que como la mínima frase que PAW considerará válida es un verbo, si FIN se teclea solo entonces ya el PARSER generará una SL de "FIN \_". En su búsqueda a través de la tabla de Respuestas, PAW encontrará la entrada que hemos visto más arriba y empezará a ejecutar los condacc.

QUIT es una condición \(la parte condicionante de la palabra condacc\). Una condición sólo decide si PAW continúa para llevar a cabo el siguiente condacto de la lista, es decir, no toma de por si ninguna acción, sino una decisión.

QUIT lo que hace es determinar si el siguiente condacto puede ser ejecutado, preguntándole al jugador "¿estás seguro?". Si él contesta NO, entonces QUIT avisa a PAW que ha hecho "algo" y éste irá en busca de otra SL \(dejando en paz QUIT\).

Esta es una forma un poco diferente de tratar las condiciones en PAW, pero QUIT es una condición bastante especial, cono verás en el futuro. Si el jugador teclea "SI" entonces QUIT no hace nada, y deja que PAW busque el siguiente condacc de la secuencia, que entonces será TURNS. TURNS es una acción que imprime "has hecho x movidas o has dado x órdenes" en la pantalla. Donde x es el número de frases que el jugador ha tecleado desde el principio del juego. Aparte de este hecho, como tú no le has dicho a PAW que deje de buscar condaccs, entonces éste continuará buscando END.

END es una acción también especial que imprime "¿apetece otro juego?, o ¿quieres jugar otra partida?" en la pantalla. Si el jugador teclea "SI" entonces END reiniciará el juego con todos los objetos en sus posiciones iniciales, etc. Si el jugador dice "NO" entonces generará un error "OK", lo cual te hará volver al menú editor de PAW. Si el menú editor de PAW no está presente \(por ejemplo, un juego ya terminado\), entonces el computador hace un reset.

**MUY IMPORTANTE:** Debes tener siempre una acción END en alguna parte del juego, porque si no, no podrás volver a la sección editora tan fácilmente cuando estés probando el juego. Tendrás que hacer uso de la tecla BREAK, la cual solamente trabaja mientras que PAW está procesando, y como no es fácil pillar a PAW haciéndolo, porque es muy rápido, te será muy difícil. Las otras entradas que ya están presentes en la base de datos, se hacen cargo de varios comandos estandarizados que los jugadores normalmente necesitarán en la aventura.

Los condaccs usados en las otras entradas se discuten más abajo.

Tú te estarás preguntando por qué estas entradas están en una tabla y no forman ya de por sí parte de PAW, si son tan necesarias en cada juego.

Pues bien mi querido saltamontes, la razón es que, aparte del hecho de que es mucho más fácil ponerlas en una tabla que en el propio juego, TU JUEGO A LO MEJOR NO LAS NECESITA, y de esta forma las puedes borrar cuando quieras.

DESC es una acción. De hecho, es la que se usa en la entrada "M \_" de la tabla. Y esta acción hace que PAW abandone la búsqueda por la tabla de respuestas y reDESCriba la localidad actual del jugador. También tiene varios sinónimos: mirar, describir, etc., en el Vocabulario.

SAVE Y LOAD son dos acciones que permiten hacer un SAVE y un RELOAD del estado actual del juego en cinta. La posición actual del juego incluye también cualquier otra pieza de información que se necesite para restaurar exactamente el juego en el mismo estado en que estaba, ello incluye los valores de las banderas, las posiciones de los objetos, y mucha más información. No debes confundir aquí los anglicismos SAVE y LOAD que hemos dejado en el vocabulario, con las acciones SAVE y LOAD. Nosotros hemos incluido también otros sinónimos, como GRABAR y CARGAR, en el Vocabulario, pero todos ellos usarán también las acciones SAVE y LOAD en la tabla de Respuestas.

Es de notar que ambos SAVE y LOAD ya de por sí hacen una acción DESC cuando han terminado. Lo cual significa que cualquier condacc que siga, será ignorado igualmente en el INPUT del jugador.

RAMSAVE Y RAMLOAD son dos acciones similares a SAVE y LOAD, excepto que ellos usan un "buffer" \(área de memoria libre\) para guardar la posición del juego. Esto significa que no tienes que andar toqueteando cintas.

Solamente una posición puede ser guardada, y como la guarda en la memoria, suponemos que sabes que si apagas el ordenador desaparecerá. Aunque de todos modos, esto debes hacérselo ver claramente al jugador en las instrucciones. También el área del buffer se pierde cuando vuelves al editor, porque tú puedes desear cambiar algún diseño en el juego entre dos textos.

El número ligado a RAMLOAD es un parámetro, y le dice al condacc cuántas de las banderas debe restaurar de un RAMSAVE previo. Esto permite que la puntuación y otras cosas se mantengan, aunque el jugador “haga trampas" en una parte muy difícil del juego usando constantemente RAMSAVE y RAMLOAD.

Ambas acciones son seguidas automáticamente por una acción DESC, puesto que a diferencia de SAVE y LOAD, ellas, por sí solas continuarán hasta el siguiente condacc.

Si a PAW se le acaban los condaccs en una lista sin haberle aclarado que ya ha hecho \(done\) algo, sencillamente "caerá" hasta el final, y al darse cuenta de esto, continuará en su búsqueda de otro SL. También dijimos que QUIT era una condición bastante especial. Para comenzar, es la única condición que busca información del jugador, y por otra parte, también le informa a PAW de que algo ha sido hecho si el jugador teclea "NO" \(es decir, que no quiere abandonar el juego\), lo cual hace que PAW comience a buscar otro nuevo SL.

MUY IMPORTANTE: una condición normal, si "falla", sencillamente hará que PAW continúe buscando en la tabla de Respuestas otra condición que haga juego con la SL.

Los otros condactos que están usados se considerarán ahora en relación con las entradas de las cuales son parte. Para simplificar nuestra explicación, debemos considerar la posición de un objeto en el juego.

Puede estar en cuatro lugares:

AQUÍ: es la localidad actual del jugador \(es el valor que se guardaba en la bandera 38, si recuerdas bien\). Tiene un valor de 255.

LLEVADO PERO NO PUESTO: Localidad 254, que es una localidad imaginaria donde se ponen todos los objetos que el jugador lleve.

PUESTOS ENCIMA: Localidad 253, que es una localidad imaginaria donde todos los objetos que el jugador lleve puestos encima son guardados.

NO PRESENTES: ¡En cualquier otro sitio! Esto también incluirá la localidad 252, que es una localidad imaginaria donde todos los objetos que aún no existen son guardados.

Resumiendo:

`Aquí =            Localidad 255`

`Llevados =        Localidad 254`

`Puestos encima =  Localidad 253`

`No presentes =    Localidad 252 = No creado todavía.`

Vamos a ver otras dos entradas en la tabla de Respuestas:

`COGE TODO   DOALL 255 (Parámetros: Localidad donde estás: Aquí)`

`COGER _     AUTOG`

  `           DONE`

Estas dos entradas son las que permiten al jugador coger cualquier objeto. Coger un objeto significa cambiar su localidad desde AQUI \(255\) a LLEVADO \(254\).

Ignoremos por ahora la entrada "coge todo" y vamos a estudiar la entrada "COGER \_". Como dijimos antes, esa línea baja significa "cualquier palabra", así que no importa qué nombre teclee el jugador en una frase que contenga el COGER. La entrada COGER \_ siempre casará \(esto es lo que se llama "cargando" o "preparando" una entrada\).

Veamos la frase "coger la manzana": la será ignorada por PAW porque no está en el Vocabulario, pero la SL será "coger manzana", y esto "cargará" la entrada "GET \_" cuando PAW encuentre este condacto.

AUTOG es una acción que AUTOmáticamente cogerá cualquier objeto que haya sido especificado por el nombre.

Es donde la tabla de Palabras-Relacionadas con Objetos viene a funcionar. AUTOG mira a través de esa tabla buscando una entrada que sea similar al nombre de la SL; cuando la encuentre \(manzana en nuestro ejemplo\) entonces sabe el número del objeto al cual se refiere \(que en el caso de la manzana es 3\).

Se asegura entonces de que la localidad actual de ese objeto sea AQUI que es \(255\) y la pasa a LLEVADA que es \(254\) y entonces imprime el mensaje "Ahora tengo el objeto \_." donde la línea baja es reemplazada por la descripción del objeto actual, por ejemplo el que acaba de marcar el AUTOG.

Si no encuentra ninguna entrada, entonces hay cinco posibilidades.

1. El jugador ha intentado coger un objeto que ya lleva o tiene puesto. En cuyo caso el mensaje "Ya tengo el \_" se imprime.
2. El jugador ha intentado coger un objeto que está en la localidad AQUI NO. En cuyo caso se imprimirá el mensaje "Aquí no hay uno de esos".
3. El jugador ha intentado coger algo que no es un objeto, pero que tiene una palabra en la tabla de Vocabulario \(por ejemplo: puerta en nuestro juego de demostración\). Esto producirá el mensaje "No puedo hacer eso".
4. El jugador ha usado una palabra que no está en el Vocabulario. Eso hace que el PARSER cree una SL de "GET \_" lo cual "carga" nuestra entrada de GET \_ de todos modos. AUTOG asume que se trata de un nombre que describe un objeto \(que puede o no puede existir\), y entonces el mensaje "No hay uno de esos aquí" se imprime.
5. El jugador no puede llevar más objetos, o el peso de este objeto sobrepasa el límite permitido para el jugador. En cuyo caso también aparecerá un mensaje que le informa de ello.

Si el AUTOG funciona, entonces PAW mira al siguiente condacc.

DONE solamente le dice a PAW que la entrada ha terminado y que debe de ir y buscar otra SL.

Ahora miraremos a la entrada GET ALL. Como habrás supuesto, esta entrada lo que hace es intentar coger todos los objetos que estén en la localidad donde estás tú.

