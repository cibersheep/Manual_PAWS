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

###### Diagrama 4

![](/assets/Diagrama04.png)

Este bucle \(loop\) se muestra en el diagrama 4 en forma de una carta de flujo que se puede seguir desde el cuadrado marcado con "comienzo". El bucle es bastante más complejo que lo que el diagrama te pueda parecer y de hecho se da una versión más completa en la guía técnica, pero de momento el diagrama 4 nos servirá.

Te aconsejamos fervientemente que vuelvas a leer los párrafos anteriores y estudies el diagrama, hasta que entiendas cómo PAW trabaja sobre una sentencia lógica antes de funcionar.

Vamos a considerar la segunda entrada de Respuestas:

Hacer I INVEN

Como habrás deducido hábilmente, esta entrada toma en cuenta otra forma de la cual el jugador puede pedir una lista de objetos. Veamos ahora la entrada que pone QUIT \_ \(para hacer esto basta con apretar cualquier tecla excepto BREAK, ESPACIO o N\):

```
FIN _     QUIT
TURNS
END
```

Bien, FIN es un verbo en el vocabulario, así que como la mínima frase que PAW considerará válida es un verbo, si FIN se teclea solo entonces ya el PARSER generará una SL de "FIN \_". En su búsqueda a través de la tabla de Respuestas, PAW encontrará la entrada que hemos visto más arriba y empezará a ejecutar los condacc.

QUIT es una condición \(la parte condicionante de la palabra condacc\). Una condición sólo decide si PAW continúa para llevar a cabo el siguiente condacto de la lista, es decir, no toma de por si ninguna acción, sino una decisión.

**QUIT** lo que hace es determinar si el siguiente condacto puede ser ejecutado, preguntándole al jugador "¿estás seguro?". Si él contesta NO, entonces QUIT avisa a PAW que ha hecho "algo" y éste irá en busca de otra SL \(dejando en paz QUIT\).

Esta es una forma un poco diferente de tratar las condiciones en PAW, pero QUIT es una condición bastante especial, cono verás en el futuro. Si el jugador teclea "SÍ" entonces QUIT no hace nada, y deja que PAW busque el siguiente condacc de la secuencia, que entonces será TURNS.

**TURNS** es una acción que imprime "has hecho x movidas o has dado x órdenes" en la pantalla. Donde x es el número de frases que el jugador ha tecleado desde el principio del juego. Aparte de este hecho, como tú no le has dicho a PAW que deje de buscar condaccs, entonces éste continuará buscando END.

**END** es una acción también especial que imprime "¿apetece otro juego?, o ¿quieres jugar otra partida?" en la pantalla. Si el jugador teclea "SI" entonces END reiniciará el juego con todos los objetos en sus posiciones iniciales, etc. Si el jugador dice "NO" entonces generará un error "OK", lo cual te hará volver al menú editor de PAW. Si el menú editor de PAW no está presente \(por ejemplo, un juego ya terminado\), entonces el computador hace un reset.

**MUY IMPORTANTE:** Debes tener siempre una acción END en alguna parte del juego, porque si no, no podrás volver a la sección editora tan fácilmente cuando estés probando el juego. Tendrás que hacer uso de la tecla BREAK, la cual solamente trabaja mientras que PAW está procesando, y como no es fácil pillar a PAW haciéndolo, porque es muy rápido, te será muy difícil. Las otras entradas que ya están presentes en la base de datos, se hacen cargo de varios comandos estandarizados que los jugadores normalmente necesitarán en la aventura.

Los condaccs usados en las otras entradas se discuten más abajo.

Tú te estarás preguntando por qué estas entradas están en una tabla y no forman ya de por sí parte de PAW, si son tan necesarias en cada juego.

Pues bien mi querido saltamontes, la razón es que, aparte del hecho de que es mucho más fácil ponerlas en una tabla que en el propio juego, TU JUEGO A LO MEJOR NO LAS NECESITA, y de esta forma las puedes borrar cuando quieras.

**DESC** es una acción. De hecho, es la que se usa en la entrada "M \_" de la tabla. Y esta acción hace que PAW abandone la búsqueda por la tabla de respuestas y reDESCriba la localidad actual del jugador. También tiene varios sinónimos: mirar, describir, etc., en el Vocabulario.

**SAVE Y LOAD** son dos acciones que permiten hacer un SAVE y un RELOAD del estado actual del juego en cinta. La posición actual del juego incluye también cualquier otra pieza de información que se necesite para restaurar exactamente el juego en el mismo estado en que estaba, ello incluye los valores de las banderas, las posiciones de los objetos, y mucha más información. No debes confundir aquí los anglicismos SAVE y LOAD que hemos dejado en el vocabulario, con las acciones SAVE y LOAD. Nosotros hemos incluido también otros sinónimos, como GRABAR y CARGAR, en el Vocabulario, pero todos ellos usarán también las acciones SAVE y LOAD en la tabla de Respuestas.

Es de notar que ambos SAVE y LOAD ya de por sí hacen una acción DESC cuando han terminado. Lo cual significa que cualquier condacc que siga, será ignorado igualmente en el INPUT del jugador.

**RAMSAVE Y RAMLOAD** son dos acciones similares a SAVE y LOAD, excepto que ellos usan un "buffer" \(área de memoria libre\) para guardar la posición del juego. Esto significa que no tienes que andar toqueteando cintas.

Solamente una posición puede ser guardada, y como la guarda en la memoria, suponemos que sabes que si apagas el ordenador desaparecerá. Aunque de todos modos, esto debes hacérselo ver claramente al jugador en las instrucciones. También el área del buffer se pierde cuando vuelves al editor, porque tú puedes desear cambiar algún diseño en el juego entre dos textos.

El número ligado a RAMLOAD es un parámetro, y le dice al condacc cuántas de las banderas debe restaurar de un RAMSAVE previo. Esto permite que la puntuación y otras cosas se mantengan, aunque el jugador “haga trampas" en una parte muy difícil del juego usando constantemente RAMSAVE y RAMLOAD.

Ambas acciones son seguidas automáticamente por una acción DESC, puesto que a diferencia de SAVE y LOAD, ellas, por sí solas continuarán hasta el siguiente condacc.

Si a PAW se le acaban los condaccs en una lista sin haberle aclarado que ya ha hecho \(done\) algo, sencillamente "caerá" hasta el final, y al darse cuenta de esto, continuará en su búsqueda de otro SL. También dijimos que QUIT era una condición bastante especial. Para comenzar, es la única condición que busca información del jugador, y por otra parte, también le informa a PAW de que algo ha sido hecho si el jugador teclea "NO" \(es decir, que no quiere abandonar el juego\), lo cual hace que PAW comience a buscar otro nuevo SL.

**MUY IMPORTANTE:** una condición normal, si "falla", sencillamente hará que PAW continúe buscando en la tabla de Respuestas otra condición que haga juego con la SL.

Los otros condactos que están usados se considerarán ahora en relación con las entradas de las cuales son parte. Para simplificar nuestra explicación, debemos considerar la posición de un objeto en el juego.

Puede estar en cuatro lugares:

AQUÍ: es la localidad actual del jugador \(es el valor que se guardaba en la bandera 38, si recuerdas bien\). Tiene un valor de 255.

LLEVADO PERO NO PUESTO: Localidad 254, que es una localidad imaginaria donde se ponen todos los objetos que el jugador lleve.

PUESTOS ENCIMA: Localidad 253, que es una localidad imaginaria donde todos los objetos que el jugador lleve puestos encima son guardados.

NO PRESENTES: ¡En cualquier otro sitio! Esto también incluirá la localidad 252, que es una localidad imaginaria donde todos los objetos que aún no existen son guardados.

Resumiendo:

```
Aquí =            Localidad 255
Llevados =        Localidad 254
Puestos encima =  Localidad 253
No presentes =    Localidad 252 = No creado todavía.
```

Vamos a ver otras dos entradas en la tabla de Respuestas:

```
COGE TODO   DOALL 255 (Parámetros: Localidad donde estás: Aquí)
COGER _     AUTOG
DONE
```

Estas dos entradas son las que permiten al jugador coger cualquier objeto. Coger un objeto significa cambiar su localidad desde AQUÍ \(255\) a LLEVADO \(254\).

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

**DONE** solamente le dice a PAW que la entrada ha terminado y que debe de ir y buscar otra SL.

Ahora miraremos a la entrada GET ALL. Como habrás supuesto, esta entrada lo que hace es intentar coger todos los objetos que estén en la localidad donde estás tú.

Explicaremos el mecanismo:

Si el jugador teclea la frase COGE TODO, el PARSER creará una sentencia lógica \(SL\) de "COGE TODO" y entonces hará pareja con la entrada presente en esta tabla y PAW pasará a ejecutar la acción DOALL.

**DOALL** es una acción que debe ser seguida con un parámetro. El parámetro nos da el número de la localidad que usaremos.

Lo que hace DOALL es buscar la lista de localidades en la cuál se encuentra cada objeto, intentando encontrar entradas que sean iguales para el parámetro que se ha dado \(que en este caso es 255, una localidad especial que significa que se use la localidad en la cual el jugador esté presente\). Cuando encuentra uno similar, o el mismo, entonces se va a la tabla objetos relacionados con palabras para encontrar la palabra del Vocabulario que describe el número del objeto.

Esta palabra se pone en la actual SL \(reemplazando el nombre todo\) y una bandera se resetea para indicar que DOALL está activo.

Luego PAW sigue mirando el resto de la tabla de Respuestas buscando una entrada que haga juego con la SL recientemente modificada.

Esta entrada será COGE \_ \(de la cuál hemos hablado antes\), que cogerá el objeto que PAW haya buscado en la tabla de Objetos.

Cuando haya terminado de hacer lo anterior, PAW se dará cuenta de que todavía permanece activo el DQALL, o sea, la bandera está seteada y vuelve otra vez a la entrada COGE TODO.

En realidad lo que hace es saltar directamente a la acción DOALL y buscar otro objeto para generar una nueva SL, y así sucesivamente para todos los objetos que estén en la localidad especificada. Cuando se acaban los objetos, entonces la bandera se resetea para demostrarle a PAW que no está activo el bucle y se le dice a PAW que busque otra SL.

Esto podría parecer un modo bastante complejo de ejecutar esa acción, pero si examinamos a las entradas similares que tratan de PONERSE, QUITARSE y DEJAR, veremos que utilizan el mismo mecanismo.

**AUTOD, AUTOW y AUTOR** trabajan de una manera muy similar a AUTOG, mientras que DOALL sencillamente se limita a cambiar la localidad actual para ejecutar las acciones. Por ejemplo, usa 254 \(LLEVADAS\) como el parámetro en la acción DROP y también en la acción WEAR \(es decir, DOALL busca todos los objetos que lleves cuando intentas dejarlos caer o ponértelos encima\); y utiliza la localidad 253 \(LLEVADO PUESTO ENCIMA\) cuando se trata de quitarse todo.

Si lo anterior te parece un poco complicado, no te preocupes de momento, porque DOALL es uno de los condactos más complejos de PAW, y poco a poco lo irás entendiendo. Sería interesante que en este momento hagas un test de la aventura, y trates todos los comandos de "dejar todo", "coger todo", etc., para que el mecanismo se te haga más claro.

### Mensajes

Antes de que continuemos con la tabla de RESPUESTAS vamos a meter algunas entradas en otra tabla que necesitaremos. Así es que, desde el menú principal, teclea \[ M \] para mensajes. La tabla de mensajes es poco complicada. El submenú es muy parecido a los de localidades y descripciones de objetos. El objetivo de los mensajes es contener todo el texto que se necesita para responder a las entradas del jugador, es decir, todo lo que está sucediendo durante el juego, \(excepto por los mensajes que ya PAW pone por su cuenta, como "Yo no puedo hacer eso", etc.\). Si tecleas la opción \[ P \] verás que ya hay una entrada presente.

Ahora vamos a poner todos los comandos para cuando el jugador intente examinar las cosas en el juego \(una de las órdenes más frecuentes y más importantes de toda la aventura\). El que un objeto sea examinable, solamente requiere que el escritor haya dejado un mensaje que dé más información sobre ese objeto, por ejemplo, en el caso de la manzana diríamos: "La manzana está madurita y muy sabrosa".

Cambia el texto del mensaje 0 \(A 0 ENTER\) e inserta los siguientes mensajes para poder examinar todas las otras cosas del juego.

```
Mensaje 1 
Es un emparedado delicioso de jamón y queso.

Mensaje 2
El billete tiene un número y el nombre de la compañía de transportes para aventureros, impreso.

Mensaje 3
El banco está anclado firmemente a una base de concreto.
```

En nuestro juego de práctica solamente usamos cuatro objetos, pero en los juegos más complicados hay que poner muchos detalles para muchas cosas, aunque no sean muy importantes en el juego, porque esto le da un toque de realismo que hace que el jugador se sienta atraído o envuelto por la atmósfera.

Así que volvamos a la tabla de RESPUESTAS \(R\) y a trabajar.

Vamos a comenzar con la manzana. La frase que el jugador tecleará será "EXAMINAR LA MANZANA" \(o EXAMINA MANZANA si es bastante vago\), y esto producirá una SENTENCIA LOGICA de "EXAMINAR MANZANA". Así que necesitaremos poner una entrada con estas dos palabras.

Teclea \(I EXAMINAR MANZANA ENTER\), PAW ignorará las letras que sobren \(que sean más de cinco\), e imprimirá la entrada en la parte de arriba de una pantalla limpia y esperará a que tu teclees la lista de condactos para esa entrada.

Pero nosotros sólo vamos a permitir que el jugador examine la manzana si está AQUI, LLEVADA o PUESTA ENCIMA \(por ejemplo, en un bolsillo\), porque la mayoría de la gente no tiene la habilidad de mirar a través de las paredes para saber si la manzana está en otra localidad. Estos tres parámetros AQUI, LLEVADO, o PUESTO ENCIMA todos se conocen como PRESENTE, y por ello basta con poner la condición PRESENT seguida del número del objeto que estemos considerando \(por ejemplo, la manzana, es el objeto 3\).

Si el objeto está presente, entonces podemos hacer aparecer nuestro mensaje 0, que describe el objeto usando la acción MESSAGE, que debe ser seguido del número del mensaje que quieras que aparezca. Finalmente lo acabaremos todo con la acción DONE para decirle a PAW que ya hemos completado lo que queríamos hacer.

Entonces teclea \(PRESENT 3 MESSAGE 0 DONE ENTER\) y PAW concestará que el mensaje está "insertado".

Ahora vamos otra vez al submenú con cualquier tecla, y tecleemos \(P EXAMINAR\) para examinar nuestra nueva creada entrada.

Por cierto, aquí conviene decir que si quieres ver la tabla desde el principio basta con teclear P. Si tecleas P seguida por I un VERBO, verás todas las entradas que pertenecen a ese verbo, y si tecleas P seguida por un VERBO y un NOMBRE verás todas las entradas del verbo y el nombre. Nuestra entrada debe parecerse a:

```
MIRAR-EXAMINAR     MANZANA    PRESENT 3
                              MESSAGE 0
                              DONE
```

Aquí tenemos un ejemplo clásico de la tabla de Respuestas, porque si la condición PRESENT 3 falla, es decir el objeto no está presente, entonces PAW continuará buscando por otra entrada diferente para hacer coincidir su SENTENCIA LOGICA.

En este caso encontrará la siguiente entrada, que es MIRAR \_, y ésta entrada producirá una descripción de la localidad en que estamos actualmente \(por medio de la acción DESC\), después de que la acción PLUS haya añadido 128 a la bandera 29.

Esto forzará a PAW a dibujar cualquier gráfico que exista en esa localidad y al mismo tiempo hacer una descripción. Sobre esto entraremos con más detalle cuando hablemos de los gráficos. Si asumimos que la manzana está realmente presente, entonces PAW continuará con el siguiente condacc y desplegará nuestra descripción de la manzana \(MENSAJE 0\), luego, la acción DONE le dice a PAW que vaya I y busque otra Sentencia Lógica, porque ya ha hecho algo \(esto previene que continúe y pase lo que pasó antes, es decir que coja la siguiente entrada que es LOOK \_\). Si hay una entrada que es incorrecta, se puede corregir tecleando por ejemplo, A MIRAR MANZANA. Sin embargo, en las tablas de Procesos puede haber más de una entrada que tenga los mismos valores de palabras, y entonces todas ellas se verán presentadas una a una para que se pueda corregir.

Si no quieres corregir una en particular, sencillamente teclea ENTER y déjala tal como está. Para borrar una entrada completamente de una tabla, lo que hay que hacer es quitar todos sus condaccs.

Por ejemplo, corrige la entrada con A, pulsa la tecla EDIT dos veces para limpiar el buffer y pulsa ENTER. Con eso la entrada quedará completamente borrada.

Pero de momento, si el jugador trata de EXAMINAR cualquier otra cosa excepto la manzana \(o cuando trata de EXAMINAR LA MANZANA y ella no está presente\) entonces, como vimos antes, se le recompensará con una descripción de su localidad actual.

Vamos a insertar las entradas para poder examinar el emparedado, el billete de autobús y el banco. Las entradas las listaremos como las verías si usaras la opción P después de que fueran tecleadas, y pondremos al lado algunos comentarios solamente para referencia. Pero no te olvides de que hay que meterlas como hiciste para introducir EXAMINAR MANZANA anteriormente.

```
MIRAR    EMPAREDADO    PRESENT 2 ;    Que el emparedado esté aquí
                       MESSAGE 1 ;    Descríbelo
                       DONE

MIRAR    BILLETE       PRESENT 4 ;    El billete está aquí
                       MESSAGE 2
                       DONE

MIRAR    BANCO         AT 4 ;         AT porque el banco no es un objeto
                       MESSAGE 3 ;    y entonces se chequea la localidad
                       DONE
```

AT es una condición que debe de ser seguida con un número de localidad y que será válida \(es decir, dejará que PAW continúe al siguiente condacto\), si el jugador está en esa misma localidad. Esto lo tuvimos que usar con el banco porque no era un objeto, pero, al ser parte de la descripción, al volver a la localidad 4 siempre estará ahí. Entonces lo que comprobamos es que el jugador esté en la localidad 4.

Usa ahora la opción T para comprobar tu aventura y ver que lo anterior funcione.

### Las tablas de procesos \(P1 : P2 : ETC.\)

Vamos a estudiar ahora la opción más potente que tiene el menú principal: las tablas de Procesos. Dijimos antes que la tabla de Respuesta era una opción especial de las tablas de Procesos, y de hecho lo es. Si tú seleccionas la opción P del menú verás un submenú muy similar al de la tabla de Respuestas, excepto que tiene dos opciones extra.

Fíjate que el título dice «Procesos 2», esto es porque hay más de una tabla de procesos en PAW, de hecho puede haber 254 tablas de procesos como veremos.

De momento hay dos tablas de Proceso en la base de datos y PAW, tal como hacía en el de Respuestas, buscará a través de ellas, pero las buscará no después de haber obtenido una sentencia lógica, sino de la siguiente forma:

Proceso 1:

El proceso 1 es chequeado inmediatamente después de que PAW ha descrito una localidad. Esto permite que la información se imprima solamente cuando el jugador llegue a esa localidad o cuando haya obtenido una redescripción.

Proceso 2:

El proceso 2 es revisado justo antes de pedir una nueva sentencia lógica al PARSER. Es usado como si fuera el «turno» de PAW para jugar.

Estudia detenidamente las formas en que PAW busca en la tabla de Proceso 1 y en la tabla de Proceso 2, ES MUY IMPORTANTE.

La diferencia principal es que en estas tablas, PAW no intenta buscar una entrada similar a una sentencia lógica, sino que EJECUTA CADA ENTRADA.

De momento, mientras jugábamos en nuestro juego de demostración, hemos tenido que terminar siempre tecleando FIN. Ahora en la "Historia Original" lo que teníamos que hacer era ayudar al pasajero a encontrar el billete de autobús antes de que éste llegase. Es obvio que podemos poner una entrada en la tabla de Respuestas para que si el jugador teclea "coger billete" \(y este estuviese presente\), se termine el juego.

```
COGER    BILLETE    PRESENT 4 ;    El billete está ahí
                    TURNS
                    END
```

pero pensamos que sería mucho más conveniente terminar el juego cuando el jugador vuelva a la parada del autobús.

Para hacer eso, primero necesitamos un mensaje que describa la llegada del autobús. Así que vamos al menú principal, seleccionemos la opción mensaje y pongamos el siguiente mensaje:

```
MENSAJE 4
El autobús llega. Le doy el billete al conductor, quien sonríe y dice: 
«siento haber llegado tarde, supongo que no ha tenido que esperar mucho».
```

Volvamos ahora a la tabla de Procesos. Aún cuando las palabras no tienen ningún significado en esta tabla, puede ser útil poner las palabras adecuadas con lo que la entrada hace. La entrada que determina el final del juego será llamada " \_ AUTOBUS" \(debemos comenzar con \_ porque PAW solamente permite el nombre Autobús en una posición que corresponda al nombre, o sea, primero el Verbo y luego el Nombre\).

Así que teclea \[ I \_ AUTOBUS ENTER \].

Las condiciones para terminar el juego son: que el jugador se encuentre en la parada del autobús \(localidad 2\) y que lleve el billete del autobús \(objeto 4\).

La primera condición será AT 2, la segunda será CARRIED 4, así que la entrada final será:

```
AT 2  CARRIED 4  MESSAGE 4  TURNS  END
```

Si se usa P, se verá que la entrada aparece de la siguiente forma:

```
_ AUTOBUS    AT 2
             CARRIED 4
             MESSAGE 4
             TURNS
             END
```

Como PAW buscará siempre en esta tabla antes de que haya un nuevo Input \(una nueva Sentencia Lógica\) por parte del jugador, cada vez que se den las condiciones descritas por CARRIED se ejecutarán las acciones Message Turns y End. Y esto es independiente de cualquier cosa que el jugador teclee para llegar a la localidad donde está la parada de autobús.

Seleccionemos ahora proceso 1 tecleando \[ S 1 ENTER \] y usemos \[P\] para examinar las entradas que ya están presentes:

```
*  _  NEWLINE
      ZERO 0
      ABSENT 0
      LISTOBJ

*  _  PRESENT 0
      LISTOBJ
```

Un asterisco «\*» significa «cualquier palabra» como significaba «\_» pero con una diferencia: siempre que PAW inserta entradas en una tabla de Procesos \(y ello incluye la de Respuestas\), las insertará según el orden de valor, primero el Verbo y segundo el Nombre \(por ejemplo, todas las entradas que se refieran a un mismo verbo irán una detrás de otra en orden ascendente según su valor de ncombre\).

PAW considera que la raya baja «\_» tiene un valor de 255 \(por lo tanto, será siempre la última entrada\). Sin embargo, considera que asterisco «\*» tiene el valor de 1 \(por lo tanto será siempre la primera entrada\).

La posición de las entradas en una tabla de procesos es muy importante. Por ejemplo, las dos entradas que hemos mencionado arriba, siempre deben estar en el mismo orden que las hemos dado. Ellas deben ser ejecutadas inmediatamente después de que se ha impreso la descripción para una localidad y por ello es por lo que usamos el asterisco, para que estén al principio de la tabla \(usamos la raya baja «\_» como si fuese un nombre para poder meter alguna entrada antes de ella, como veremos en su momento\).

Veamos por qué se ponen esas dos entradas. Como PAW ejecuta siempre todas las entradas que hayan en Proceso 1 y Proceso 2 \(suponemos que te darás cuenta de que lo hará de cualquier forma, porque una entrada que lleve \* \_ hará pareja con cualquier Input del jugador, es decir, con cualquier Sentencia Lógica\) la acción NEWLINE siempre será ejecutada.

**NEWLINE** Imprime espacios hasta el final de la línea actual. Esto permite que el mismo color de Papel continúe hasta el final de la línea sin tener que teclear todos los espacios. Su principal objetivo aquí es asegurar que cualquier texto que se imprima lo sea en la siguiente línea, porque PAW no pone automáticamente una línea en blanco después de la descripción de las localidades. La guía técnica nos mostrará cómo usar este efecto para modificar una descripción de localidad, para reflejar los cambios que haya.

De ahora en adelante las dos entradas deben ser consideradas como una pareja, su propósito final es hacer una lista de los objetos que estén en la localidad actual. Veamos cómo: PAW usa la bandera 0 para determinar si hay luz para que el jugador pueda ver \(esto no ha sido utilizado de momento en nuestra demostración\), si no hay luz, la bandera tendrá un valor diferente de 0 y PAW contestará «está muy oscuro para ver» en vez de hacer una descripción de la localidad. En este caso los objetos que están presentes no deben aparecer en lista puesto que se supone que el jugador no los puede ver.

El objeto 0 siempre es tomado por PAW como el objeto que provee luz \(objeto 0 = fuente de luz\), esto es por lo que en nuestro juego de demostración, el objeto 0 es una antorcha encendida. Si este objeto está presente cuando en el juego se supone que está oscuro \(o sea, que la bandera 0 no sea 0\) entonces, la sola presencia del objeto 0 tendrá preferencia sobre el hecho de que no haya luz, y los objetos deben ser descritos.

Estos dos últimos párrafos son muy importantes y debes releerlos hasta estar seguro de que los entiendes.

Así pues, vemos que las dos entradas nos dan un ejemplo de cómo se usa PAW para crear una situación OR. Por ejemplo, haz una lista de los objetos si hay luz o \(OR\) el objeto 0 está presente.

**ZERO** Es la primera condición que hemos encontrado hasta ahora que chequea el estado de una bandera. Zero 0 será positiva si la bandera cero contiene 0, lo cual significa que hay luz.

**ABSENT** Chequea que el objeto 0 no esté presente \(es el opuesto a la condición PRESENT, todas las condiciones tienen su opuesto. Por ejemplo, AT tiene su opuesto en NOTAT, etc\). Como la siguiente \* \_ va a hacer un listado de los objetos, si el objeto 0 \(la fuente de luz\) está presente, no queremos que la primera entrada de \* \_ sea positiva también \(la cual tiene en cuenta una hipotética situación, en la cual haya luz y el objeto 0 también esté presente, y entonces se haría una lista de los objetos dos veces\).

**LISTOBJ** Hará una lista de todos los objetos que estén presentes en la localidad actual. Si ninguno está presente no hace nada. Sería un poco tonto decir «Puedo ver nada».

Nota importante: Repasa bien lo anterior, puesto que es una característica de PAW que necesitarás usar con frecuencia en tus juegos.

Ahora vamos a poner una forma más adecuada de pasar de la pantalla de introducción al principio del juego en la parada de autobús. Lo haremos de la siguiente forma:

```
*   *   AT 0
        ANYKEY
        GOTO 2
        DESC
```

Inserta esta entrada en Procesos 1 \(asegúrate de que todavía está seleccionado\) usando \[I \* \* ENTER\]. Esto nos introduce dos nuevos condactos.

**ANYKEY** Imprime "Pulse tecla para continuar" en la parte inferior de la pantalla, y espera a que pulses una tecla antes de permitirle a PAW continuar.

**GOTO** Debe ser seguido por un número de localidad y mueve al jugador a esa localidad \(efectivamente, pone la bandera 38, la bandera que marca la localidad actual del jugador, al valor dado\). Como no hace nada más, debe ir seguida por un DESC para que PAW describa la nueva localidad. Esta entrada entonces lo que hace es que la pantalla del título aparezca, luego espera por el toque de tecla para pasar al juego en la localidad correcta.

Ahora es el momento de ir a la tabla de conexiones y quitar la entrada que pusimos desde la localidad 0 porque ya no se necesita.

Hagamos un test del juego para ver las dos entradas en acción. Si tecleásemos de una sola vez toda la frase:

OESTE, OESTE, ARRIBA, COGER EL BILLETE. ABAJO, ESTE Y ESTE.

tendríamos el juego terminado, con su mensaje de si quieres volver a jugar otra vez. Si no es así, vuelve a chequear las entradas en las tablas de Procesos 1 y 2.

### Objetos dentro de algo

Vamos a ver la habilidad de la bolsa para contener objetos. Ello requiere algunas entradas en la tabla de Respuestas, porque vamos a permitir al jugador que MIRE DENTRO DE LA BOLSA, así que necesitamos un nuevo mensaje: «En la bolsa hay:». Por lo tanto, selecciona la opción de MENSAJES e INSERTADO \(debe ser Mensaje 5\).

Otra vez a la tabla de RESPUESTAS.

Vamos a dotar al jugador de la opción de decir "Poner todo dentro de la bolsa", además de "poner \(objeto\) en la bolsa". Podemos usar exactamente el mismo sistema que hicimos con coger y dejar todo. Poner es un sinónimo de dejar, por lo que la Sentencia Lógica que estamos buscando debe ser PONER \_ \(es decir, cuando el jugador está tratando de poner o dejar algo\), pero si el jugador incluye EN LA BOLSA como parte de su frase, haremos que PAW ponga el objeto DENTRO DE LA BOLSA. Esto significa que hay que pasar por alto la entrada PUT \_ que ya está presente, si las palabras extras incluidas en la Sentencia Lógica especifican que el objeto es la bolsa.

Para insertar esta entrada antes de una que ya esté presente, hay que hacer lo siguiente: normalmente PAW insertará otra entrada con el mismo valor de palabra después de cualquier entrada que ya esté presente. Es posible forzarlo a que lo haga antes especificando un número después de la inserción. \(Ojo: muy importante\).

Intenta \[I PUT DEJA \_ 0 ENTER\], esto instruye a PAW para que ponga la entrada antes de la entrada número 1, puesto que le hemos dado un valor 0 antes de ENTER, y como la entrada número 1 es el PUT \_ que ya existe, PAW la pondrá antes de ella.

Ahora pongamos los condactos que necesitamos y que son:

```
PREP EN  NOUN2  BOLSA  PRESENTI 1  AUTOP 1  DONE.
```

Esto es un ejemplo de cómo nos aseguramos de que ciertas partes de la frase sean lo que nosotros queremos.

**PREP** Es una condición que debe ser seguida por una preposición del vocabulario. Las preposiciones son palabras que se usan antes de un Nombre para mostrar su relación con otras palabras de la frase. En este caso la condición será favorable o acertará si el jugador ha usado en \(o dentro\) como parte de la frase.

**NOUN2** Es una condición que debe ser seguida por un nombre del vocabulario. Será positiva si el jugador ha usado bolsa en la frase como segundo nombre. Combinado con la entrada previa tiene el efecto de hacer que PAW pare de buscar en las tablas de condacto a menos que la Sentencia Lógica fuera PONER \_ EN o DENTRO DE LA BOLSA donde la raya baja sería cualquier objeto.

**AUTOP** Debe ser seguida por el número de una localidad. Nosotros hemos puesto la localidad 1 aparte con un propósito especial desde el comienzo de este ejemplo. Esto es, la hemos usado como si estuviera dentro de la bolsa. Por lo tanto AUTOP, de la misma forma que AUTOD, busca en la tabla de Objetos-Palabra por un nombre que haga pareja con el primer nombre de la Sentencia Lógica. Cuando ha encontrado uno, lo pone en la localidad que le hayamos dado, respondiendo «He puesto el o la \_ en o dentro de la bolsa».

La entrada DEJA TODO ya existente, también se hace cargo de PONERLO TODO EN LA BOLSA, porque no especifica que EN LA BOLSA sea parte de la Sentencia Lógica, por lo tanto se disparará en ambas ocasiones, y en ambos casos 254 es la localidad desde la cual vendrán los objetos.

Ahora para COGER un objeto FUERA DE LA BOLSA \(o sacar un objeto de la bolsa\), debemos teclear una entrada similar, que haga nula la entrada ya presente de COGER \_ . Así que tecleemos \[COGER \_ O ENTER\], con ello nos aseguramos que será puesta antes.

```
PREP FUERA  NOUN2  BOLSA  PRESENT 1  AUTOT 1  DONE
```

**AUTOT** Debe ser seguido por un número de localidad, que debe ser de la cuál venga el objeto que se va a sacar. \(En este caso, la 1\).

Por otra parte, para hacer la versión SACAR TODO necesitamos también otra entrada. De momento COGER TODO causa un DOALL 255, la cual es la posición actual del jugador. Para que saquemos todo de la bolsa necesitamos generar un contador de los objetos que estén dentro de ella \(localidad 1\), así que hay que insertar una entrada nueva de coger todo, que salte por encima de la existente. Tecleemos \[I COGER TODO 0 ENTER\]:

```
PREP FUERA  NOUN2  BOLSA  DOALL 1
```

Todo esto se puede obviar usando los verbos sacar y meter \(pero es importante que lo veamos de esta forma por si hay que hacer alguna entrada complicada como esta\).

También debemos poner una entrada que le permita al jugador EXAMINAR DENTRO DE LA BOLSA o MIRAR DENTRO DE LA BOLSA, y será:

```
MIRAR BOLSA  PREP  DENTRO
             MESSAJE 5
             LISTAT 1
             DONE
```

**LISTAT** Debe ser seguido por un número de localidad y listará todos los objetos presentes en esa localidad. Si no hay objeto presente dirá «ninguno»; así que si tecleamos con la bolsa vacía, la respuesta será «En la bolsa hay: nada», lo cual es correcto, en oposición con LISTOBJ que veíamos que no ponía nada porque tiene un uso mucho más frecuente. Hagamos un test de la aventura para ver que de verdad podemos poner y sacar todo de la bolsa.

