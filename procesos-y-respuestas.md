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

### El pajarito

El juego de práctica que hemos hecho es bastante fácil de resolver \(bastante tontito, la verdad\). Así que le vamos a añadir un poco de complejidad creando dos caracteres que vayan vagando por nuestro pequeño mundo. Estos caracteres son llamados PSI, o Caracteres Seudo Inteligentes, porque es obvio que aunque no pueden pensar, deben . parecerle al jugador como si lo hiciesen. Un PSI consiste principalmente en una colección de mensajes, banderas y entradas en tablas de procesos. Verás que con unas pocas entradas simples se pueden crear efectos sorprendentemente reales.

La creación de un complejo PSI puede tomar mucho más tiempo, pero en general sigue los mismos principios que los que vamos a hacer con los nuestros: un pajarito y un perrito. El pájaro se pone para complicar el escenario de la siguiente manera: Cogerá el billete al principio del juego \(normalmente se le daría una localidad no usada como contenedor de los objetos que lleve el pájaro, pero nosotros usaremos la localidad 252, puesto que tenemos solamente un PSI que puede tener un objeto\).

De modo que el jugador debe convencer al pajarito para que deje caer el billete. El intentar quitárselo o cogerlo dará el mensaje «No puedo hacer eso», y que el pajarito se vaya volando hacia otra parte.

El pajarito también dará la paliza volando entre el pabellón de música y una ramita del árbol, y esto lo hará a intervalos regulares. La única manera de convencer al pajarito para que deje caer el billete de autobús es dejar caer el emparedado en la misma localidad.

Lo primero que hay que hacer es ir a la tabla de Objetos Inicialmente En \[la tabla I\] y cambiar el objeto 4 a no creado, es decir, darle al objeto 4, que es el billete, el valor de 252.

Esto hace que el objeto no exista como un objeto, porque lo lleva el pajarito en el pico. En el vocabulario insertemos también los nombres pajarito o pájaro y perro. Supondremos que el pájaro es 22 y el perro es 21, perro = 21, pájaro - 22, porque sus valores como palabras serán usados para poner las entradas en el orden correcto en las tablas de Procesos.

Después, insertamos los siguientes mensajes. Podemos usar tinta verde \(en MODO EXTENDIDO, CAPS SHIFT + 4\) para los mensajes, no olvidando volver a poner tinta blanca al final \(MODO EXTENDIDO, CAPS SHIFT + 7\).

#### MODO EXTENDIDO + CAPS SHIFT + NUMERO = EL COLOR DE LA TINTA

```
Mensaje 6
El pajarito deja caer el billete para coger el emparedado.

Mensaje 7
El pajarito se lleva velozmente el billete.

Mensaje 8
El pajarito me ignora.

Mensaje 9
Un pajarito anda rondando por aquí.

Mensaje 10
El pajarito tiene un billete en su pico.

Mensaje 11
Un pequeño pajarito se posa en la hierba.

Mensaje 12
El pajarito está ahora en la rama del árbol.

Mensaje 13
El pajarito ve al perro y sale pitando.

Mensaje 14
El pajarito se va.
```

Luego pondremos los mensajes que vaya a usar el perro, pero ahora debemos seleccionar la tabla de Procesos y prepararnos para otras de las virguerías de PAW.

### SUBPROCESOS

En una aventura de verdad que contenga varios PSI y un montón de acciones, las tablas de Procesos 1 y 2 pronto acabarán llenas, y se hace cada vez más difícil trabajar de esta forma. Entonces viene el momento de dejar que las otras tablas de Procesos comiencen a actuar. Estas pueden ser llamadas desde las tablas de Procesos 1 y 2 o de la tabla de Respuestas, y usadas como una extensión de la tabla desde la cual fueron llamadas.

El llamar a otro proceso hace que PAW guarde en memoria dónde estaba en el momento de ser llamado, y continuará actuando en la misma forma en que lo estaba haciendo. Por ejemplo, si se llamó desde una tabla de Respuestas, PAW tratará de hacer coincidir la Sentencia Lógica actual con cualquier otra entrada. Pero si es llamado desde una tabla de Procesos, sea la 1 o la 2, PAW sencillamente ejecutará cada entrada. \(ESTO ES MUY IMPORTANTE\).

Por otra parte, cuando algo es DONE en el Proceso llamado, PAW volverá a la tabla original y continuará trabajando. Por lo tanto se pueden hacer acciones bastantes complejas mediante el uso de los subprocesos. Los usuarios que sepan algo de programación reconocerán fácilmente que son sencillamente subrutinas.

Cuando PAW está en un subproceso, es posible que sea llamado para actuar en otro subproceso \(¿un sub-subproceso?\), y así se puede continuar con sub-sub-sub hasta un valor de 10. Es decir, las subrutinas pueden ser anidadas hasta un valor de 10. Si se intenta ir más lejos saldrá la frase "Limit Reached", o sea Límite Alcanzado.

En este momento no vamos a usar un subproceso muy complicado, solamente uno simple, y lo haremos para tener en cuenta todas las chorraditas del pájaro.

Usando \[B\] se comienza un nuevo subproceso y PAW automáticamente te localizará el siguiente número libre. De momento deberíamos estar comenzando el proceso 3. Como solamente hay unas pocas entradas en la tabla, usaremos el mismo par de palabras \("\_ PAJARO"\), aún cuando hay que tener en cuenta que al escribir tu juego debes de usar otras palabras que te recuerden lo que hace cada entrada.

La bandera 11, será una bandera de "trabajo", porque contiene un valor que se usa solamente como comparación.

La bandera 12, llevará el número de la localidad actual del pájaro.

La bandera 5, es una bandera especial, porque si tiene un valor diferente de 0, disminuirá 1 cada vez que PAW ejecute una acción, es decir, cada vez que PAW revise la tabla de Proceso 2. Es lo que se llama una bandera autodecreciente.

En este caso usaremos la bandera 5 para contar el número de turnos que han pasado en el juego. Un turno del juego es toda una vuelta del circuito grande en el diagrama 4, y de momento, esto pasa cada vez que el jugador teclea una frase.

El pajarito cambiará de localidad cada tres frases, lo que creará una especie de apariencia de acción independiente de lo que teclea el jugador.

Ahora, vamos a insertar las siguientes entradas \(sin los comentarios, como hicimos antes\). En cada entrada tenemos una explicación de su propósito y también explicaremos cualquier nuevo condacto que se use:

Primero hay que determinar si el pájaro va a salir pitando;., esto pasará cuando la bandera 5 tenga valor 0 \(empezará a contar desde 3\). Entonces, si el billete está en la misma localidad que la del pájaro, será destruido \(puesto que la localidad 252 indica que el pájaro lo tiene\) y si el jugador está en la misma localidad que el pájaro, se le dirá que el pájaro se ha llevado el billete.

Tienes que darte cuenta de que el pájaro sigue con sus ciclos de movimientos aunque el jugador no lo vea. De hecho en el mundo de PAW un árbol se cae aunque no haya nadie para verlo. Así de real es.

```
_ PAJARO    COPYOF    4    11    ;Copia la localidad del objeto 4 (el billete)
                                 a la bandera 11.
            SAME      11   12    ;y mira si está en la misma localidad que el pájaro.
            ZERO      5          ;¿Va a volar el pájaro?
            DESTROY   4          ;E1 pájaro coge el billete.
            SAME      12   38    ;¿Está el pájaro en la misma localidad que el jugador?
            MESSAGE   7          ;Díselo al jugador.
```

Fíjate, no hay acción DONE porque queremos que PAW haga cada entrada, una detrás de otra, siempre que se cumplan los requisitos de las condiciones de ellas. La tabla anterior te muestra cómo se pueden mezclar condiciones y acciones para crear nuevas condiciones.

**COPYOF**

Es una acción que debe ser seguida por el número de un objeto y una bandera. Lo que hace es que copia la localidad actual del objeto que se especifique, en la bandera especificada. La usamos en esta situación para ver si el billete está en la misma localidad que el pájaro.

**SAME**

Es una condición que compara el contenido de dos banderas, y que es favorable o positiva si ambas son del mismo valor.

**DESTROY**

Es una acción que pone un objeto especificado en la localidad 252 \(localidad no creada\).

Ahora vamos a crear dos posibles movimientos para el pájaro. Si el pájaro está en el pabellón de música y la bandera 5 ha llegado a 0, entonces hay que mover el pájaro, setear la bandera 5 a tres otra vez y decirle al jugador que el pájaro se ha ido, si está en la misma localidad. Y lo mismo si el pájaro está en la rama.

```
_ PAJARO     EQ    12    18    ;¿Está el pájaro en la rama?
             ZERO  5           ;¿Es tiempo de volar?
             LET   12    5     ;Mover el pájaro al pabellón
             LET   5     3     ;Tres frases antes de moverse.
             AT    8           ;¿Está el jugador también aquí?
             MESSAGE 14        ;Dile que el pájaro ha volado.

_ PAJARO     EQ    12    5     ;EL pájaro está en el pabellón.
             ZERO  5           ;¿Es tiempo de volar?
             LET   12    8     ;Mover el pájaro a la rama
             LET   5     3     ;Deja 3 frases antes de moverlo
             AT    5           ;¿Está el jugador también aquí?
             MESSAGE 14        ;Dile que el pájaro ha volado.
```

**EQ**

Es una condición que debe ser seguida por un número de bandera y otro valor, y que será positiva si la bandera contiene ese valor. En este caso \(EQ 12 8\) está comprobando si el pájaro está en una localidad específica.

**LET**

Es una acción que también es seguida por una bandera y un valor. Y pone ese valor en la bandera. Ya henos tenido en cuenta el vuelo del pájaro. Ahora vamos a poner sus llegadas, y si llega a una localidad en la que esté el jugador, hay que decírselo.

```
_ PAJARO     EQ    5    3     ;¿Acaba de volar el pájaro?
             SAME  12   38    ;¿Está en la localidad del jugador?
             AT    5          ;¿o en el pabellón de música?
             MESSAGE 11       ;Ha aterrizado en la hierba.

_ PAJARO     EQ    5    3     ;¿Acaba de volar el pájaro?
             SAME  12         ;¿Está en la localidad del jugador?
             AT    8          ;¿o está en la rama?
             MESSAGE 12       ;Aterrizó en la rama.
```

Ahora, si el pájaro tiene el billete en su pico debemos decírselo al jugador.

```
_ PAJARO    EQ    5    5    
            SAME  12   28    
            ISAT  4    252    ;¿E1 billete no ha sido creado?
            MESSAGE 10        ;Tiene el billete en su pico.
```

**ISAT**

Es una condición seguida de un objeto y el número de una localidad y es positiva si el objeto está en la localidad especificada. Finalmente, si el emparedado está en la misma localidad que el pájaro, el pájaro dejará el billete para coger el emparedado. Esta entrada no tiene nada que ver con la bandera 5, así que será buscada cada vez que PAW vaya al Proceso 2. Por lo tanto, si el jugador deja caer el emparedado después de que el pájaro haya llegado, la secuencia correcta aún se llevará a cabo.

```
_ PAJARO    COPYOF  2     11   ;Emparedado.
            SAME    11    12   ;¿En la misma localidad que el pájaro?
            ISAT    4     252  ;¿Lleva el billete en el pico?
            COPYFO  12    4    ;Empieza a caer el billete.
            SAME    12    38   ;¿Está el jugador también por ahí?
            MESSAGE 6          ;Díselo
```

**COPYFO**

Es una acción que copia el contenido de una bandera específica a la localidad actual del objeto específico. También hay acciones COPYFF y COPYOO que son fáciles de comprender. Así completamos las rutinas de control del pajarito. Pero necesitamos una entrada en el Proceso 2 para llamar a todas esas rutinas en cada ciclo, así que busquemos en la tabla 2 y pongamos la entrada que llama a todo el subproceso, es decir, la entrada "madre".

```
_PAJARO    PROCESS     3
```

lo que hará que PAW ejecute nuestros controles de pájaro cada vez que pase por ahí. Ahora debemos asegurarnos de que el pájaro empieza en la localidad correcta y que el jugador sabe que el pájaro esta ahí cuando la localidad se describe \(o empezará a ver mensajes acerca de un pájaro dando la paliza sin haber tenido ninguna descripción de que existe tal pájaro\). Así que seleccionemos el Proceso 1 \(que ya sabemos que se llama después de cada descripción de localidad\) y vamos a corregir la entrada existente con \* \* poniéndole un \[LET 12 8\], lo cual hará que el pájaro esté en la rama al principio del juego. La entrada modificada debe ser:

```
* *             AT    0
                ANYKEY
                LET   12    8    ;E1 pájaro está en la rama (localidad 8)
                GOTO  2        
                DESC
```

Y también hay que poner la siguiente entrada en la tabla de Procesos, para que le diga al jugador que hay un pajarito, y que tiene el billete.

```
_ PAJARO         SAME    12    38
                 MESSAGE 9
                 ISAT    4    252
                 MESSAGE 10
```

Por último seleccionaremos la tabla de Respuestas e insertaremos la entrada:

```
COGER BILLETE    SAME    12    38    ;¿Está el pájaro en la misma localidad?
                 ISAT    4     252   ;¿Con el billete en el pico?
                 CLEAR   5           ;Esto lo fuerza a volar
                 NOTDONE             ;"No puedo hacer eso".
```

Esta entrada se disparará antes de la entrada `GET _`  y previene la respuesta "No hay uno de esos aquí" si el pájaro está presente con el billete.

**CLEAR**

Es una acción que va seguida por un número de bandera, y que pone esa bandera a 0. En este caso hará que el pájaro salga pitando, simulando su miedo a una gran mano que desciende sobre él para coger su preciada posesión.

**NOTDONE**

Es una acción similar a DONE, pero que engaña a PAW pensando que no has hecho nada y por lo tanto hace imprimir el mensaje "No puedo hacer eso".

Y ahora, vamos al momento de la verdad. Hay que probar el juego para ver si el pájaro vuela del pabellón de música a la rama. Juega un rato para ver si el pájaro continúa con su existencia vagabunda. Después trata de dejar caer el emparedado en la misma localidad. Date cuenta, de que si no coges el billete antes de que el pájaro se pire, el pájaro lo cogerá otra vez.

Y menos mal que acabamos con el bendito pájaro. Es complicado, pero te enseñará un montón sobre el PAW.

#### EL PERRO

Este perro lo ponemos para complicar el juego un poco más. Simplemente seguirá al jugador donde quiera que vaya y espantará al pajarito. Comoo no se espera que el perro se suba al árbol, debemos impedir que el jugador pueda tentar al pájaro con el emparedado desde la rama. Para hacer eso dispondremos que cualquier objeto que se suelte desde la rama del árbol caiga hasta el suelo. El jugador se puede desembarazar del maldito perro poniéndole la cadena y amarrándola al banco. Además, el jugador puede "hablar" al perro, lo cuál le dará otro medio de desembarazarse de él diciéndole que se SIENTE o que se QUEDE.

Antes de examinar las entradas en las tablas de Procesos y Respuestas, necesitamos tener el control del perro por medio de las siguientes palabras en el vocabulario y mensajes en la tabla de Mensajes.

```
Verbos    Nombre
----------------
ATAR      34
DESATAR   35
SENTAR    36
QUEDAR    36
VEN       37
AQUI      37
```

Los números te demuestran que sentarse y quedarse son lo mismo, y que también usamos un Nombre y un Verbo con el mismo número.

```
Mensaje 15
El _ cae al suelo al pie del árbol.
```

No se debe cambiar el color de este mensaje, y el que pongamos una raya baja en él tiene un propósito especial, del cuál ya hablaremos más adelante.

Los demás mensajes que hablen del perro pueden ser puestos de cualquier otro color, por ejemplo magenta \(MODO EXTENDIDO, CAPS SHIPT + 3\) no olvidando nunca volver al blanco al final de cada uno de ellos. El color del mensaje le permite al jugador saber exactamente a quién se refiere cada mensaje.

```
Mensaje 16
El perro me mira con amor.

Mensaje 17
El perro está aquí.

Mensaje 18
El perro me sigue moviendo la cola.

Mensaje 19
El perro va arrastrando la correa.

Mensaje 20
El perro está atado al banco con una correa.

Mensaje 21
Confiadamente, el perro me deja ponerle la correa alrededor del cuello.

Mensaje 22
He amarrado el perro al banco.

Mensaje 23
¿A quién se lo digo?

Mensaje 24
El perro se sienta tranquilo.

Mensaje 25
He desatado el perro del banco.
```

No hay verdadera necesidad de hacer la rutina para el perro en una tabla de Procesos separados, porque solamente hay una entrada, pero lo haremos por si quieres ampliar el juego más tarde.

La bandera 13 contendrá la localidad actual del perro.

La bandera 14 contendrá varios indicadores:

```
0    si el perro está libre para andar por ahí.
1    si el perro tiene la correa alrededor del cuello.
2    si el perro está atado al banco.
252  si el perro está sentado muy tranquilo.
```

Desde la tabla de Procesos, con \[B\] empezamos una nueva tabla de Procesos \(debe ser la tabla número 4\) y ponemos una sola entrada:

```
_ PERRO    NOTSAME  13    38   ;¿No está el perro donde está el jugador?
           LT       14    2    ;¿Todavía se puede mover?
           NOTAT    8          ;¿E1 jugador no está arriba del árbol?
           COPYFF   38    13   ; Mueve el perro a la localidad del jugador.
           MESSAGE  18         ;Y dile que lo atosigue.
```

Suponemos que eres capaz de entender qué es NOTSAME, NOTAT y COPYFF, en caso negativo, en la guía técnica te explicaremos para qué sirve cada una.

**LT**

Es una condición que es positiva o favorable si la bandera especificada contiene un valor MENOR QUE el valor especificado. En este caso \[LT 14 2\] solamente será positivo o acertado si la bandera 14 tiene un valor menor de 2.

Ahora vamos a la tabla de Procesos 2:

```
_ PERRO    PROCESS    4
```

es decir, que estás usando la tabla de Procesos 2 para enviar a PAW a la tabla de Procesos 4. La entrada “\_ Perro", \(si usamos \[P\] para mirar a la tabla\), debe estar antes de la entrada del pajarito \(si no es así, es que has puesto las palabras del vocabulario de una forma diferente de la que dijimos\). Es para asegurar que el perro se mueva a la nueva localidad del jugador antes de que el pájaro sea comprobado.

Similarmente a como hicimos con el pájaro, se requieren entradas en la tabla de Procesos 1, para informarle al jugador que el perro anda por ahí rondando:

```
_ PERRO    SAME    13    38    ;¿El perro está en la misma localidad?
           MESSAGE 17          ;Díselo al jugador.
           EQ      14    1     ;¿con la correa?
           MESSAGE 19          ;sí, díselo al jugador.

_ PERRO    SAME    13    38    
           EQ      14    2     ;¿Está el perro amarrado al banco?
           MESSAGE 20        
           
_ PERRO    SAME    13    38    
           GT      14    2     ;255 es mayor que 2 así que
           MESSAGE 24          ;Dile al jugador que el perro sentado.
```

Ya que estamos en la tabla de Procesos 1, modifiquemos la entrada \* \* para que también tenga \[LET 13 2\] \(antes del GOTO\), esto hace que el perro empiece en la parada de autobús. Ahora, para que el perro asuste al pajarito, necesitamos una entrada extra en la tabla de Procesos 3. Pero debe ir delante de la entrada que decide que el pájaro deje caer el billete y después de la entrada que hace que el pájaro vuele. Así nos aseguramos que el pájaro volará con el billete si lo tiene y lo deja si no lo tiene.

Por lo tanto, necesitamos insertar otra entrada antes de la sexta. Usaremos \[I \_ PAJARO 6\] para hacerlo.

```
_ PAJARO    SAME    12    13   ;EL pájaro y el perro estén en la misma localidad.
            LET     12    8    ; Sólo en el pabellón de música
            LET     5          ;Muévelo a la rama, espera 3 frases.
            AT      5          ;¿Está el jugador en el Pabellón de Música?
            MESSAGE 13         ;Dile que el pájaro se ha ido.
```

El número de cualquier inserción o corrección tiene un valor máximo de 255. O sea, que no debes de insertar más de 256 entradas con el mismo tipo de palabra \(lo cual sería de todos modos bastante poco manejable\), si quieres retener la habilidad de seguir insertando en cualquier parte de la lista. El último cambio en la tabla de Procesos es insertar un subproceso que luego llamaremos desde la tabla de Respuestas para que se haga cargo de hablar al perro. El mecanismo es muy simple. Si el jugador incluye una frase "\(" "\)" en su sentencia de INPUT, entonces el parser guardará memoria del lugar donde esté y seguirá descifrando la frase entre comillas. Hay una acción llamada PARSE que instruye a PAW para que decodifique la cadena de palabras que el jugador haya tecleado, haciendo entonces la Sentencia Lógica. Lo lógico es hacer esto en un subproceso porque PAW tratará de buscar una similitud entre la nueva Sentencia Lógica y el resto de la frase.

Entonces comencemos una nueva tabla de Proceso \(que debe ser la 5\) e insertemos las siguientes entradas:

```
* *          PARSE            ;Convierte una cadena a SL.
             MESSAGE 16       ;No es una frase válida así que...
             DONE             ;El perro no te entiende.

SIENTATE _   ZERO    14       ;¿El perro no está amarrado?
             SET     14       ;Ahora está sentado quieto.
             MESSAGE 24       ;Díselo al jugador \(si está en el mismo lugar que el perro\)
             DONE

VEN _        EQ      14   255 ;El perro debe de estar sentado
             CLEAR   14       ;Ahora está normal.
             MESSAGE 13       ;E1 perro te sigue.
             DONE

_ AQUI       EQ      14   255    
             CLEAR   14        
             MESSAGE 13        
             DONE            

_ _          MESSAGE 16        ;Cualquier otra cosa.
```

La última entrada se usa para obviar el vocabulario tan limitado que entiende el perro, haciéndole que para cualquier otra frase mueva la cola, por eso se pone la última con `_ _`.

Recordar que PAW va buscando en toda la tabla de Procesos, y si no encuentra una igual a la que busca caerá en esta última entrada de `_ _`.

**PARSE**

PARSE le permite a PAW continuar buscando condactos si no encuentra una Sentencia válida. Hay que tener cuidado aquí, puesto que la actual Sentencia Lógica puede estar un poco enrevesada \(el parser intentará sacar algún significado de todos modos\) así que normalmente se debe insertar algún mensaje como "Parece no entender" o algo similar, y después un DONE para volver a la acción anterior.

Si se forma una Sentencia válida PAW empezará a buscar las siguientes entradas por una similar, como hacía en la tabla de Respuestas. PARSE debe ser solamente usada en un subproceso que sea llamado desde la tabla de Respuestas, puesto que no tiene ningún significado en otra tabla. Date cuenta de cómo las entradas VEN y AQUI se hacen cargo de una cantidad de frases que el jugador puede usar después de que el perro esté sentado, porque ambas tienen, una delante y otra detrás, la palabra comodín, o sea, la raya.

Y por último, la entrada "`_ _`" coge cualquier sentencia que se haya metido en la cadena y para la cual el perro no tenga una respuesta especifica.

Selecciona la tabla de Respuestas para insertar algunas entradas extra que controlen el habla y el dejar caer objetos del árbol.

La primera de todas es la entrada que hace que los objetos que se dejen en el -árbol caigan al suelo. Esto debe ir entre la entrada que se hace cargo de poner objetos dentro de la bolsa y la entrada normal de "DEJAR \_". Entonces \[I PONER \_ l\] nos situará en esa posición. La entrada es:

```
PONER _      AT      8        ;Que el jugador esté en la rama.
             WHATO            ;Ya hablaremos de ello.
             LT      51  255  ;¿Es un objeto válido?
             EQ      54  254  ;¿Es un objeto que llevas encima?
             MESSAGE 15       ;Avisa que está al pie del árbol
             PUTO    7        ;La pone ahí.
             DONE
```

Esto es un ejemplo de cómo se crea una acción automática, viene a ser lo mismo que un AUTOG, etc.

**WHATO**

Es una acción que mira el primer Nombre de la Sentencia Lógica actual en la tabla Objeto-Palabra, y la convierte en el número de un objeto. Este número se pone entonces en la bandera 51. La bandera 51 siempre contiene el número del último objeto que se ha usado, o el último del que PAW tiene referencia, y siempre que esté seteada, las banderas asociadas \(números 54 y 57\) también se setean.

La bandera 54 lleva la localización actual del objeto. Es conveniente que mires el manual técnico para las banderas 51, 54 y 57.

