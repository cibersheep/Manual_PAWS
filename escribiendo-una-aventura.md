## Escribiendo una aventura

### Enfoque previo

Es muy importante un buen planteamiento si se quieres crear una aventura con un nivel aceptable. De nada sirve sentarse a la máquina y empezar a teclear esperando la inspiración. Lo único que se conseguirá es un desorden de números y palabras y sin otro recurso que volver a empezarlo todo de nuevo.

Para ilustrar el método recomendado, crearemos y desarrollaremos una simple aventura desde el inicio de la idea hasta el resultado final.

¡¡¡Recuerda salvar tu BD con regularidad!!!

### El guión inicial

Esa idea inicial es siempre la parte más difícil al crear cualquier cosa. Una historia original puede dar al juego un interés mucho mayor que la vieja historia de rescatar a la consabida princesa. Guiones hay de todas clases y de todo tipo, pero aconsejamos que si intentas basar la historia en una película, libro o cómic, y luego intentas usarla comercialmente, te asegures antes de obtener el permiso del autor o de los actuales dueños de copyright.

En nuestro ejemplo tomaremos los problemas que pueden ocurrirle a un pasajero en su vuelta a casa:

Mientras estaba en la parada del autobús, el billete de subida fue arrebatado por un golpe de viento y luego cogido y llevado por un pajarito hasta un cercano parque.

El ordenador juega la parte del pasajero a quien se debe dirigir para encontrar el BILLETE antes de que llegue el autobús.

### Diseño del juego

Ahora que la idea está más clara, es importante hacer un boceto del área de juego; en nuestro ejemplo sería algo parecido al [diagrama 2](#diagrama-2).

Es de notar que la zona de juego debe estar cerrada de una manera lógica, o el jugador no entenderá por qué no puede ir en una dirección si no hay nada que le impida el paso.

Para el ordenador, una aventura consiste en un determinado número de apartados o localidades que el jugador debe visitar; es ahora el momento de decidir qué zonas del boceto se tomarán como localidades y numerarlas individualmente.

Se debe intentar hacer una escala consistente o lógica \(a menos que el juego sea ilógico intencionadamente\), evitando que con un solo paso se vaya de una localidad a otra que aparentemente queda a varias millas de distancia.

La localidad 0 debe ser reservada siempre como pantalla de títulos y dejaremos libre también la 1 para darle un uso especial; por lo tanto comenzaremos desde la 2 hacia arriba. En nuestro ejemplo hemos escogido 7 localidades:

2\) parada del autobús

3\) en el jardín

4\) cerca del banco

5\) en el pabellón de música

6\) el estanque

7\) al lado del árbol

8\) arriba del árbol

Ahora podemos empezar las descripciones de las localidades. Deben ser lo más imaginativas posible, pero en estilo corto e interesante. Hay que procurar mantener una misma forma de verbo todo el tiempo, generalmente primera \(yo\) o segunda \(tú\) persona, o pronto el jugador tendrá una seria crisis de identidad. Sea cual sea la forma elegida, debe de estar de acuerdo con los Mensajes del Sistema \(ver más adelante\).

###### Diagrama 2

![](/assets/diagrama02-entero.png)

Para claridad y ver mejor los posibles movimientos haremos el mapa del [diagrama 3](#diagrama-3).

###### Diagrama 3

![](/assets/Diagrama03.png)

Pantalla de muestra del menú

![](/assets/pantalla-muestra-menu.png)

### EMPEZANDO A TECLEAR

#### Localidades

Selecciona la opción L en el menú principal. Un pequeño submenú te mostrará las opciones para insertar o corregir \(amend\). Como todos los menús se parecen, examinaremos estas opciones para familiarizarnos con ellas. \(Ver el esquema de menú del dibujo anterior\).

Cualquier cosa tecleada aparecerá en la parte inferior de la pantalla, como siempre. Las zonas en inverse nos indican lo que hay que teclear para obtener las funciones que figuran a la derecha. Por ejemplo: La opción P nos dará una descripción de la localidad elegida, en este caso será la 0, que siempre existe para simplificar el trabajo interno del PAW, y podremos ver la inclusión de colores, etc., dentro del texto, para destacar ciertas palabras. Ese texto debe ser reemplazado por nuestra introducción, así que debe ser corregido.

Con cualquier tecla volvemos al submenú y tecleando A 0 \(no olvidar el espacio\) veremos el texto de la localidad elegida, pero con el cursor al final para una posible edición. Para limpiar TODO el texto teclea EDIT \(cap. sh. + 1\) dos veces y obtendrás una localidad limpia para trabajar. Nota: tener en cuenta que con teclear CAPS SHIFT + 6 \(flecha hacia abajo\), dos veces, lo que se obtiene es un stop en input, con mensaje de error en la parte inferior de la pantalla. Basta apretar cualquier tecla para volver al último menú usado, pero dejando el texto original intacto. Esta es la diferencia entre Edit y el 6.

#### Colores

El texto que utilizaremos como pantalla de introducción va a incluir algunos colores para destacar el título; así que teclea once espacios, con lo cual quedará centrado.

Tecleando EXTRA MODE \(que es Symbol Shift + Caps Shift en el 48K\), los números del 0 al 7 darán el papel ocolor de fondo. Si nosotros queremos que el título tenga un fondo rojo apretaremos el 2.

Teclea el título, que en nuestro caso es "EL BILLETE", y ahora debemos volver al color original de papel, así que teclea EXTRA y 0 para obtener el negro.

Necesitamos poner una línea en blanco entre el título y el texto, pero no podemos teclear ENTER porque esto termina la edición, por lo tanto, necesitamos UN CODIGO EXTENDIDO DE CONTROL DE PANTALLA \(CECP\); estos son códigos de 0 a 7 que tienen varios usos dentro del PAW. CECP 7 da automáticamente un newline CENTRO o nueva línea\).

Para usar un CECP hay que hacer una pequeña trampa con el Editor de la siguiente forma: Primero teclea EXTRA y selecciona el color blanco \(7\), luego teclea DELETE \(borrar\) una sola vez; con ello borrarás el control del papel pero dejara el número 7, por lo tanto, como dijimos antes, el cursor saltará al principio de una nueva línea. Haz esto otra vez para dejar una línea en blanco y teclea el resto de la introducción. Ten en cuenta que PAW hace un formateo automático del texto.

	TEXTO: \[Mientras esperaba el autobús una ráfaga de viento se llevó mi billete. ¿Puede Vd. ayudarme a encontrarlo?\].

Cuando hayas terminado teclea ENTER para finalizar la edición y luego cualquier tecla para volver al submenú.

Con la opción P se puede ver el texto todavía sin formatear, pues esto sólo se ejecuta mientras se juega el juego.

Con L se imprimirá el texto. Si parece que el ordenador se cuelga teclea BREAK \(CAPS SHIFT + ESPACIO en 48K\) para volver al menú, y entonces busca en la guía técnica más información sobre la impresora.

Con I se crea una nueva localidad. No hace falta teclear un número detrás porque PAW automáticamente le asigna el próximo que esté libre. De momento dejaremos la localidad 1 sin usar, así que sólo teclea I + ENTER y ahora tendrás una localidad virgen para usar. Con ENTER y cualquier tecla volverás al submenú.

Ahora teclea I + ENTER otra vez para insertar la localidad 2 y luego poder teclear el texto que la describe.

Debido al formateo automático hay que teclear siempre los espacios aunque sea al final de la línea, porque si no el programa tomará dos palabras como si fuera una sola larga. Los espacios sobrantes serán suprimidos luego durante el juego.

**REGLA:** Teclea siempre el espacio entre dos palabras o entre un punto final y el comienzo de la próxima frase, aunque ese espacio esté al comienzo de una nueva línea de pantalla. Luego será suprimido por el formateador si es necesario.

		TEXTO LOCALIDAD 2: \[Estoy en la parada del autobús en una calle de dirección Norte - Sur. Al Oeste queda un parque cuya verja de hierro está abierta\].

Vuelve al submenú con ENTER \(desde ahora omitiremos el uso de la palabra ENTER\) suponiendo que con tu inteligencia habitual has captado la onda.

Ahora es el momento de demostrar cómo PAW previene y avisa cuando una orden no es válida: teclea I + ENTER \(juraíto que es la última vez que te lo recuerdo\) y como resultado tendrás una parpadeante interrogación después del 3. Esto se debe a que PAW se ha dado cuenta de que no se necesita ningún número después de la opción insertar.

Por otra parte PAW posicionará siempre el cursor tan cerca al problema como pueda, en este caso con un solo DELETE quitaremos el número \(no te preocupes por el espacio que queda pues PAW ignora cualquier espacio superfluo.

Ahora ENTER proporciona la localidad 3 en blanco.

	TEXTO LOCALIDAD 3: \[La hierba sobre la cual camino está muy bien cuidada. Hacia el Norte hay un cómodo banco y hacia el Este queda un estanque\].

	TEXTO 4: \[Estoy en un camino de grava que va de Este a Oeste, muy cercano a un cómodo banco. Hacia el Sur hay un I cuidado césped y hacia el Norte hay un pabellón de música\].

	TEXTO 5: \[Estoy en el pabellón de música. Al Sur hay un camino de grava\].

	TEXTO 6: \[El sol crea bellos efectos de luz en la superficie del estanque, mecida por una suave brisa. Hay un camino al Norte que termina en un lloroso sauce. Al Este queda un cuidado césped\].

	TEXTO 7: \[Estoy al lado de un sauce llorón. Al Sur queda el estanque\].

	TEXTO 8: \[Estoy sentado en una rama del sauce, con una visión panorámica del parque; lejos, al Este, más allá de la verja del parque, puedo ver la parada del autobús\].

Usa P para chequear lo que has tecleado y cuando la pantalla se llene de texto aparecerá el mensaje "más..." en la parte inferior de la pantalla. Si entonces pulsas cualquier tecla \(excepto BREAK,ESPACIO o N\) aparecerá otra pantalla llena de texto y así hasta llegar al final donde aparece el mensaje "PULSE CUALQUIER TECLA".

BREAK, ESPACIO y N causarán un BREAK error y te permiten salir del listado. Vale. Ahora tenemos varias localidades pero no hay modo de llegar de una a otra. Eso nos deja dos opciones por ver: la opción B, con la cual se inicia una nueva página de memoria en los 128K. De momento no tocarla, porque el juego de práctica cabe sobradamente en la página 0. Sobre la opción B, trataremos más extensamente en la guía técnica.

Con la opción Z, como agudamente habrás deducido, volveremos al menú principal.

#### Conexiones

Desde el menú principal, tecleando \(C\) vamos a un menú similar al de las localidades. Date cuenta que las entradas pueden ser corregidas con \(A\), presentadas en pantalla con \(P\), o sacadas por impresora con \(L\).

La razón de esto es que PAW ya ha insertado una línea en blanco en la tabla de conexiones cada vez que tú has puesto una nueva localidad. Si usas la opción \(P\) para mirar a la tabla verás que ya hay entradas en blanco para localidades 0 a 8.

Si miramos otra vez nuestro mapa veremos las conexiones que se requieren entre localidades. Desde la localidad 2 \(parada autobús\) necesitaremos solamente el movimiento OESTE que nos llevará a la localidad 4.

Por lo tanto, hay que teclear \(A 2\) para corregir la entrada de la localidad 2, y luego teclear \(OESTE 4\) lo cual instruye a PAW que, cuando el jugador teclee la palabra OESTE y esté en la localidad 2, debe ser movido a la localidad 4.

Si usamos ahora la opción \(P\) para examinar la entrada que acabamos de hacer \(date cuenta de que con P 2 se imprimirán solamente las entradas a partir de la localidad 2 hacia arriba\), entonces encontrarás que la entrada esté más o menos:

	Localidad 2 OESTE to 4

	etc.

Esto es porque PAW sabe que 0 es un sinónimo de OESTE \(un sinónimo es una palabra que significa lo mismo\). PAW usará siempre el sinónimo más corto.

Para la localidad 3, necesitamos 3 conexiones: NORTE \(a 4\), OESTE \(a 6\), NOROESTE \(a 7\). Las conexiones que quedan sai las siguientes:

	Localidad 4 \(N 5\), \(E 2\), \(S 3\) \(SO 6\) \(0 7\)

	Localidad 5 \(S 4\) , \(SO 7\)

	Localidad 6 \(N 7\), \(NE 4\), \(E 3\)

	Localidad 7 \(ARRIBA 8\), \(NE 5\), \(E 4\), \(SE 3\), \(S 6\)

	Localidad 8 \(BAJAR 7\)

Ahora corrige las entradas de la localidad 0 para que cualquier movimiento nos lleve a la localidad 2, donde comenzamos el juego \(hay una forma mejor de hacer esto, pero necesitamos para ello usar una tabla que todavía desconocemos, y que ya te mostraremos más adelante\).

Ahora solamente falta teclear \(A 0\) ENTER \(N 2\) ENTER, y ya nos indica que de la localidad 0 al NORTE iremos a la 2.

Comprueba todas estas entradas mirando el mapa hasta que estés seguro de que todo sea correcto.

Recordamos que usando la Z se puede volver al menú principal y que desde el menú principal con

la opción S se puede grabar en cinta la base de datos actual.

También puedes, con la opción E, examinar el resto del menú que no cabe en la pantalla.

### JUGANDO EL JUEGO

Ha llegado el momento de intentar probar nuestro juego. La opción requerida para ello es \(T\) en el menú principal. Te preguntará si quieres diagnóstico o no, por el momento sólo tecleemos N y ENTER, porque no sabemos todavía para qué sirven los diagnósticos.

Ahora debe de aparecer la pantalla con el título que tecleamos al comienzo. La línea de INPUT se usa para poner las órdenes para que el PAW las interprete y ejecute tus acciones de acuerdo con la información que le hayas dado cuando escribiste el juego.

De momento, solamente le hemos dicho hacia donde nos puede llevar cuando una dirección se teclea. Eso es lo que intentaremos probar. Ahora empecemos el juego correctamente tecleando NORTE desde la localidad 0 y, por supuesto, ENTER.

Recordemos que con DELETE podemos corregir cualquier error que hayamos cometido en la línea de INPUT.

Veremos entonces que la pantalla se limpia y que la descripción para la localidad 2 aparece. Si ello no ocurre, probablemente la entrada en las conexiones esta equivocada. No te preocupes, porque se puede volver otra vez al editor tecleando ABANDONAR o RETIRAR \(que es el comando que el PAW conoce desde el principio\) y respondiendo S a la pregunta que el PAW hace y contestando N a la siguiente pregunta de que "si quieres probar otra vez" el juego o no.

Vuelve a las conexiones y corrige lo necesario.

Ahora hay que probar moverse entre las localidades viendo todos los movimientos posibles \(toma nota de cualquier movimiento erróneo para poderlo corregir cuando vuelvas al Editor\).

También es tiempo de hablar de algunas órdenes que PAW ya tiene dentro y que conoce. Por ejemplo, tecleando M o MIRAR se repite otra vez la descripción de la localidad, lo que es muy útil para el jugador si hay un montón de texto en una descripción que ya ha hecho SCROLL.

Tecleando I o INVENTARIO harás una lista de los objetos que lleves en este momento, por ahora llevarás solamente un objeto desde el comienzo, pero no podrás hacer nada con él.

Por cierto, en este momento cabe destacar que, puesto que PAW acepta hasta 120 palabras juntas, se puede hacer un recorrido por todo el juego tecleando todas las direcciones de una vez. Inclusive durante el recorrido puedes hacer un inventario.

### OBJETOS

Objeto es cualquier cosa que el jugador puede manipular dentro del juego, por ejemplo: una manzana que puede comer, una llave que puede usar para abrir una puerta, una espada para pelear, etc.

En nuestro juego, que es bastante simple, usaremos los siguientes objetos \(no todos ellos tendrán una función en el juego finalizado\):

	Objeto 0 	una antorcha encendida.

	Objeto 1 	una bolsa.

	Objeto 2 	un emparedado.

	Objeto 3 	una manzana.

	Objeto 4 	un billete de autobús.

	Objeto 5 	una piedra.

	Objeto 6 	un anorak.

	Objeto 7 	una antorcha apagada.

Muy Importante: La antorcha se trata como dos objetos separados. Cambiaremos del uno al otro cuando el jugador la apague o la encienda.

Otro punto a destacar es el hecho de que PAW, al hacer un inventario, muestra la descripción de los objetos eliminando la primera palabra \("una"\). Para evitar esto, se deberá insertar al comienzo de cada descripción un código de cambio de color, por ejemplo \[EXTRA y 0\] para poner el paper negro. Este truco evita que PAW se coma la primera palabra.

La opción 0 del menú principal sirve, como muy agudamente habrás deducido, para poner las descripciones de los objetos, de una forma muy similar a como hemos puesto las descripciones de las localidades.

Veremos que también existe un objeto 0 si se usa la opción P, para hacer una lista de ellos. Por lo tanto hay que corregir esta entrada del objeto 0 tecleando \(A 0\) y usando un color de tinta diferente. Por ejemplo, si queremos usar el color Cyan, hay que pasar al modo extendido o extra en el 128 y luego teclear al mismo tiempo CAPS SHIFT + 5.

No te olvides de volver al color blanco otra vez, esto se logra con el modo extendido y luego CAPS SHIFT y 7 al mismo tiempo. Esto debe hacerse al final de cada texto.

Volvamos al menú principal para que le podamos decir a PAW más cosas sobre nuestros objetos. Con la opción I tenemos dónde está cada objeto inicialmente, es decir, cuando la aventura comienza.

Vemos que no hay opción de insertar, puesto que eso ya queda hecho automáticamente por PAW cuando en la tabla 0 se ha puesto un objeto. Date cuenta que corregir \(Amend\) \(A\) tiene dos parámetros; el número del objeto y su posición.

Esta posición tiene varios valores especiales que son muy importantes \(son localidades que no existen\):

	252 	es para objetos no creados, por ejemplo, todavía no existen dentro del juego.

	253 	tiene todos los objetos llevados encima \(puestos\) por el jugador.

	254 	tiene todos los objetos llevados por el jugador, pero no puestos encima.

Por ejemplo, si queremos hacer de la antorcha encendida un objeto no creado hay que teclear \[A 0 252\] y como antes estaba como objeto llevado, el mensaje AMEND que significa corregido será impreso para mostrar que PAW ha hecho la corrección.

Tecleemos ahora las siguientes posiciones iniciales, pero sin poner los comentarios que van después del punto y coma \(;\).

Luego, cuando hayas terminado, usa la opción P para corregirlos.

	Objeto 1 	2; 		porque la bolsa se encuentra en la parada del autobús.

	Objeto 2 	254; 	porque el jugador lleva el emparedado.

	Objeto 3 	254; 	y la manzana.

	Objeto 4 	8; 		significa que el billete está arriba del árbol.

	Objeto 5 	3; 		una piedra que está en la hierba.

	Objeto 6 	253; 	porque el jugador lleva puesto encima el anorak.

	Objeto 7 	254; 	y lleva consigo la antorcha apagada.

Ahora vamos a decirle a PAW más cosas acerca de los objetos; por ejemplo, su peso relativo, o si son capaces de contener a otros objetos, o si el jugador puede llevarlos puestos encima. Volvemos al menú principal y tecleamos la opción X, con ello pasamos al menú de peso de objetos, que también nos permite poner los otros dos atributos \(contenedor y llevable encima\). Como siempre, PAW ya ha creado una entrada en esta tabla para todos los objetos que se han insertado previamente. De hecho ya le ha dado a cada objeto el peso de una unidad, no contenedor, y no llevable. Esto lo asigna a cada objeto por defecto \(por defecto significa el que PAW le da, si tu no le das ningún valor\).

Necesitamos probablemente corregir el anorak y la bolsa, puesto que el jugador es capaz de llevar puesto encima el anorak \(de hecho el jugador está haciendo esto desde el principio cuando comienza el juego\) y la bolsa debe ser capaz de contener otros objetos. Además, el anorak y la bolsa son mucho más pesados \(relativamente\) que los otros objetos y hay que cambiarles su valor a 3 unidades cada uno.

Cuando se teclea A para corregir aparecen 3 valores; uno es el número del objeto, otro es el peso unitario del objeto, y finalmente el tercero son los otros atributos, que pueden ser:

	0 = 	ninguno.

	1 = 	contenedor para otros objetos.

	2 = 	el jugador puede ponérselo y quitárselo.

	3 = 	un contenedor que puede ser puesto y quitado \(ejemplo: unos pantalones que tienen un bolsillo\).

Volvamos a nuestra bolsa, \(objeto 1\) que es un contenedor y pesa 3 unidades. Entonces necesitamos teclear \[A 1 3 1\] \(NO TE OLVIDES DE PONER LOS ESPACIOS\).

El anorak no tiene bolsillos \(por lo menos en este juego no los tiene\), pero puede ser llevado encima y quitado, por lo tanto hay que teclear \[A 6 3 2\].

Usemos la opción P para examinar las entradas que hemos hecho, y deben ser:

	Objeto 0 	Pesa 1

	Objeto 1 	Pesa 3 		C ; 		C significa que es un contenedor. \(1\)

	Objeto 2 	Pesa 1

	Objeto 3 	Pesa 1

	Objeto 4 	Pesa 1

	Objeto 5 	Pesa 1

	Objeto 6 	Pesa 1 		WR ;  	WR significa que se puede poner y quitar. \(2\)

	Objeto 7 	Pesa 1



Ahora podemos probar la aventura otra vez para asegurarnos de que todos los objetos estén donde tienen que estar. Pero todavía no se puede hacer nada con ellos, necesitamos decirle a PAW qué palabra describe cada objeto.

También es el momento de hacer un SAVE de la Base de Datos, pero teniendo el cuidado de que sea en una nueva sección de la cinta y usando un diferente número de versión.

