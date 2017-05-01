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

###### Pantalla de muestra del menú

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

```
Localidad 2 OESTE to 4

etc.
```

Esto es porque PAW sabe que 0 es un sinónimo de OESTE \(un sinónimo es una palabra que significa lo mismo\). PAW usará siempre el sinónimo más corto.

Para la localidad 3, necesitamos 3 conexiones: NORTE \(a 4\), OESTE \(a 6\), NOROESTE \(a 7\). Las conexiones que quedan sai las siguientes:

Localidad 4 \(N 5\), \(E 2\), \(S 3\), \(SO 6\), \(0 7\)

Localidad 5 \(S 4\), \(SO 7\)

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

También es tiempo de hablar de algTecleando I o INVENTARIO harás una lista de los objetos que lleves en este momento, por ahora llevarás solamente un objeto desde el comienzo, pero no podrásunas órdenes que PAW ya tiene dentro y que conoce. Por ejemplo, tecleando M o MIRAR se repite otra vez la descripción de la Tecleando I o INVENTARIO harás una lista de los objetos que lleves en este momento, por ahora llevarás solamente un objeto desde el comienzo, pero no podráslocalidad, lo que es muy útil para el jugador si hay un montón de texto en una descripción que ya ha hecho SCROLL.

Tecleando I o INVENTARIO harás una lista de los objetos que lleves en este momento, por ahora llevarás solamente un objeto desde el comienzo, pero no podrás hacer nada con él.

Por cierto, en este momento cabe destacar que, puesto que PAW acepta hasta 120 palabras juntas, se puede hacer un recorrido por todo el juego tecleando todas las direcciones de una vez. Inclusive durante el recorrido puedes hacer un inventario.

### OBJETOS

Objeto es cualquier cosa que el jugador puede manipular dentro del juego, por ejemplo: una manzana que puede comer, una llave que puede usar para abrir una puerta, una espada para pelear, etc.

En nuestro juego, que es bastante simple, usaremos los siguientes objetos \(no todos ellos tendrán una función en el juego finalizado\):

```
Objeto 0     una antorcha encendida.

Objeto 1     una bolsa.

Objeto 2     un emparedado.

Objeto 3     una manzana.

Objeto 4     un billete de autobús.

Objeto 5     una piedra.

Objeto 6     un anorak.

Objeto 7     una antorcha apagada.
```

Muy Importante: La antorcha se trata como dos objetos separados. Cambiaremos del uno al otro cuando el jugador la apague o la encienda.

Otro punto a destacar es el hecho de que PAW, al hacer un inventario, muestra la descripción de los objetos eliminando la primera palabra \("una"\). Para evitar esto, se deberá insertar al comienzo de cada descripción un código de cambio de color, por ejemplo \[EXTRA y 0\] para poner el paper negro. Este truco evita que PAW se coma la primera palabra.

La opción 0 del menú principal sirve, como muy agudamente habrás deducido, para poner las descripciones de los objetos, de una forma muy similar a como hemos puesto las descripciones de las localidades.

Veremos que también existe un objeto 0 si se usa la opción P, para hacer una lista de ellos. Por lo tanto hay que corregir esta entrada del objeto 0 tecleando \(A 0\) y usando un color de tinta diferente. Por ejemplo, si queremos usar el color Cyan, hay que pasar al modo extendido o extra en el 128 y luego teclear al mismo tiempo CAPS SHIFT + 5.

No te olvides de volver al color blanco otra vez, esto se logra con el modo extendido y luego CAPS SHIFT y 7 al mismo tiempo. Esto debe hacerse al final de cada texto.

Volvamos al menú principal para que le podamos decir a PAW más cosas sobre nuestros objetos. Con la opción I tenemos dónde está cada objeto inicialmente, es decir, cuando la aventura comienza.

Vemos que no hay opción de insertar, puesto que eso ya queda hecho automáticamente por PAW cuando en la tabla 0 se ha puesto un objeto. Date cuenta que corregir \(Amend\) \(A\) tiene dos parámetros; el número del objeto y su posición.

Esta posición tiene varios valores especiales que son muy importantes \(son localidades que no existen\):

```
252     es para objetos no creados, por ejemplo, todavía no existen dentro del juego.

253     tiene todos los objetos llevados encima \(puestos\) por el jugador.

254     tiene todos los objetos llevados por el jugador, pero no puestos encima.
```

Por ejemplo, si queremos hacer de la antorcha encendida un objeto no creado hay que teclear \[A 0 252\] y como antes estaba como objeto llevado, el mensaje AMEND que significa corregido será impreso para mostrar que PAW ha hecho la corrección.

Tecleemos ahora las siguientes posiciones iniciales, pero sin poner los comentarios que van después del punto y coma \(;\).

Luego, cuando hayas terminado, usa la opción P para corregirlos.

```
Objeto 1     2;       porque la bolsa se encuentra en la parada del autobús.

Objeto 2     254;     porque el jugador lleva el emparedado.

Objeto 3     254;     y la manzana.

Objeto 4     8;       significa que el billete está arriba del árbol.

Objeto 5     3;       una piedra que está en la hierba.

Objeto 6     253;     porque el jugador lleva puesto encima el anorak.

Objeto 7     254;     y lleva consigo la antorcha apagada.
```

Ahora vamos a decirle a PAW más cosas acerca de los objetos; por ejemplo, su peso relativo, o si son capaces de contener a otros objetos, o si el jugador puede llevarlos puestos encima. Volvemos al menú principal y tecleamos la opción X, con ello pasamos al menú de peso de objetos, que también nos permite poner los otros dos atributos \(contenedor y llevable encima\). Como siempre, PAW ya ha creado una entrada en esta tabla para todos los objetos que se han insertado previamente. De hecho ya le ha dado a cada objeto el peso de una unidad, no contenedor, y no llevable. Esto lo asigna a cada objeto por defecto \(por defecto significa el que PAW le da, si tu no le das ningún valor\).

Necesitamos probablemente corregir el anorak y la bolsa, puesto que el jugador es capaz de llevar puesto encima el anorak \(de hecho el jugador está haciendo esto desde el principio cuando comienza el juego\) y la bolsa debe ser capaz de contener otros objetos. Además, el anorak y la bolsa son mucho más pesados \(relativamente\) que los otros objetos y hay que cambiarles su valor a 3 unidades cada uno.

Cuando se teclea A para corregir aparecen 3 valores; uno es el número del objeto, otro es el peso unitario del objeto, y finalmente el tercero son los otros atributos, que pueden ser:

```
0 =     ninguno.

1 =     contenedor para otros objetos.

2 =     el jugador puede ponérselo y quitárselo.

3 =     un contenedor que puede ser puesto y quitado \(ejemplo: unos pantalones que tienen un bolsillo\).
```

Volvamos a nuestra bolsa, \(objeto 1\) que es un contenedor y pesa 3 unidades. Entonces necesitamos teclear \[A 1 3 1\] \(NO TE OLVIDES DE PONER LOS ESPACIOS\).

El anorak no tiene bolsillos \(por lo menos en este juego no los tiene\), pero puede ser llevado encima y quitado, por lo tanto hay que teclear \[A 6 3 2\].

Usemos la opción P para examinar las entradas que hemos hecho, y deben ser:

```
Objeto 0     Pesa 1

Objeto 1     Pesa 3         C ;         C significa que es un contenedor. \(1\)

Objeto 2     Pesa 1

Objeto 3     Pesa 1

Objeto 4     Pesa 1

Objeto 5     Pesa 1

Objeto 6     Pesa 1         WR ;      WR significa que se puede poner y quitar. \(2\)

Objeto 7     Pesa 1
```

Ahora podemos probar la aventura otra vez para asegurarnos de que todos los objetos estén donde tienen que estar. Pero todavía no se puede hacer nada con ellos, necesitamos decirle a PAW qué palabra describe cada objeto.

También es el momento de hacer un SAVE de la Base de Datos, pero teniendo el cuidado de que sea en una nueva sección de la cinta y usando un diferente número de versión.

#### Vocabulario

Tiene un menú más complejo que los que hemos visto hasta ahora, pero la mayoría de las entradas son sólo recordatorios de las opciones a tu disposición.

El Vocabulario es una lista de las palabras que PAW puede reconocer si el jugador las teclea durante el juego. Por lo tanto, cualquier palabra que no esté en esta tabla no tendrá ningún efecto. Hemos dejado un vocabulario inicial que ya contiene los verbos, nombres, etc., más usados en las aventuras.

Cada entrada para una palabra consiste en un máximo de cinco letras que, o bien cubren la palabra completa, por ejemplo NORTE, o san las cinco primeras letras de otra palabra más larga, por ejemplo describir, seguido del valor para esa palabra y del tipo de palabra \(por ejemplo: Nombre, Verbo, etc.\).

El usar solamente cinco letras para guardar una palabra reduce la cantidad de memoria requerida para guardar el vocabulario entero; también reduce la longitud de los INPUTS del jugador, y acelera la búsqueda de palabras por el propio PAW. Además, cinco letras son suficientes para establecer una diferencia entre la mayoría de las palabras usadas corrientemente.

El menú permite la INSERCION y el BORRADO \(delete\) de palabras; el LISTADO de entradas hechas para cada tipo de palabras, y la inspección de sinónimos.

Si tecleamos S OESTE veremos que PAW muestra el sinónimo O también. Si tecleamos P 2 tendremos una lista de todos los nombres que hay actualmente en PAW \(los números que corresponden a cada tipo de palabra se muestran al lado derecho del menú\). También encontraras que PAW tiene ya en su Vocabulario todas las direcciones del compás y algunas otras útiles.

Necesitamos ahora aumentar el número de NOMBRES para poder poner las palabras que representan nuestros objetos.

Todos los nombres con un valor menor de 50 son nombres propios, por ejemplo: nombres de personajes o lugares, pero más específicamente, para PAW son nombres que no se pueden cambiar por la terminación verbal lo o la.

Explicándolo mejor: para mayor rapidez PAW detecta cuáles palabras son nombres propios \(menos de 50\) y cuales pertenecen a objetos manejables \(mayores de 50\).

En la frase "coge el martillo, golpea a Manolo en la cabeza y déjalo", si has dado a Manolo un valor menor de 50 y a martillo uno mayor, PAW entiende que el la final del verbo se refiere al martillo. Otro ejemplo: en la frase "dale a Carlos una tortilla y quítasela", entenderá que el la final se refiere a la tortilla.

El lo o la también puede ponerse antes del verbo con iguales resultados.

Otro hecho importante es que las palabras con valor inferior a 20 son nombres, y que si PAW no encuentra un verbo en la frase los convertirá temporalmente en verbos.

Por ejemplo: la palabra NORTE es un nombre y puede ser usado en la frase "ir al norte"; pero también puede ser tecleada sola, en cuyo caso como tiene un valor inferior a 20 se comportará como un verbo \(o sea, que te vas al norte\).

Finalmente, las palabras con un valor menor de 14 se tomarán siempre como palabras-movimiento \(cualquier palabra que sea una dirección\) y sirven para determinar el mensaje que PAW imprimirá si no puede hacer nada con esa frase \(por ejemplo, determinará si te responde con un "no puedo" o "no puedo ir en esa dirección".

Hay que notar que esto de "menor de 14 es palabra-movimiento" se aplica tanto a verbos como a nombres convertibles en verbos.

Puesto que todos nuestros objetos son manejables, les daremos un valor mayor de 49.

```
ANTORcha         50

BOLSA            51

EMPARedado       52

MANZAna          53

BILLEte          54

PIEDRa           55

ANORAk           56
```

Usa la opción I para insertar estas 7 palabras como nombres \(tipo 2\). Por ejemplo, teclea \[ I ANT0R 50 2 \], etc.

Con P 2 se puede comprobar que estos nombres están ahora en el Vocabulario.

También necesitaremos usar adjetivos para diferenciar entre las dos antorchas. Con P 3 podemos ver los adjetivo que PAW ya conoce.

Si no están ENCENDIDO y APAGADO insértalas procurando darles un número alto, pues son poco usados, y así PAW no tendrá que pasar a través de ellos cada vez que busque una palabra más común, por ejemplo un nombre o un verbo.

Todos los números desde el 2 al 254, están disponibles para cualquier tipo de palabra y no hay limitación en el uso de sinónimos.

Si tratas de insertar una palabra que ya está presente, PAW te lo avisará, lo mismo que si tratas de borrar una que no esté presente.

Ten en cuenta que PAW solo tomará las primeras 5 letras cuando te refieras a una palabra e ignorará el resto.

Luego volveremos al Vocabulario, pero ahora vamos a decirle a PAW qué palabras definen nuestros objetos. Porque hasta ahora hemos descrito cada objeto, cuánto pesa, y dónde comienza, pero no le hemos dicho a PAW qué palabra identifica cada objeto.

Vuelve al menú principal y así podremos continuar con otra opción.

#### Palabras para los objetos

La opción W es una tabla donde las palabras que están en el vocabulario se asocian con un objeto particular. En esta tabla solamente se puede corregir, imprimir en pantalla, o imprimir en impresora, puesto que PAW ya ha insertado una entrada en blanco para cada objeto cuando se hizo su descripción en la tabla de texto para objetos. Así pues, tecleando P aparecerán 8 entradas en blanco para nuestros objetos.

La tabla de asociación de palabras y objetos permite poner un nombre y un adjetivo asociados al número del objeto. Nuestros objetos requerirán las siguientes entradas:

```
Objeto     0     ANTORCHA ENCENDIDA

Objeto     1     BOLSA _

Objeto     2     EMPAREDADO _

Objeto     3     MANZANA _

Objeto     4     BILLETE DE AUTOBÚS \_

Objeto     5     PIEDRA \_

Objeto     6     ANORAK \_

Objeto     7     ANTORCHA APAGADA
```

Este signo especial " \_ " significa que no hay palabras, o sea que entenderá cualquier palabra. Siempre hay que teclear \_ \(este signo\) si no hay un adjetivo que describe al nombre. Suponemos que con tu sagacidad habitual habrás notado que no se puede insertar un objeto, sino solamente corregirlo \(A\).

#### Diagnóstico

Con T del menú principal se selecciona la opción de probar el juego, o sea, hacer un test de la aventura.

Primero te pregunta si quieres o no quieres diagnóstico, si tecleas "si", aparecerá el titulo y la introducción, y en la parte de abajo se pide un INPUT al jugador.

El que hayas contestado que quieres diagnóstico no tiene efecto aparente todavía, pero si tecleas ENTER antes de cualquier otra cosa, el cursor desaparece y aparecerá una línea parecida a:

```
Flag 38 = 0 ?
```

con flag se refiere PAW a una bandera, en este caso la 38, la que lleva el número de localidad presente.

PAW contiene 256 de estas banderas, y en cada una se puede situar un número de 0 a 255. Se usan para indicar el estado en parte del juego.

Por ejemplo, si decides que la bandera 11 se ponga en 1 cuando la puerta del parque esté cerrada, y haga un clear a 0 cuando esté abierta, esto servirá de marcador para que luego puedas dejar pasar o no al jugador cuando teclee ENTER.

Es decir, si la bandera estuviera a 0 podría pasar, y si la bandera estuviera a 1 le darías el informe de que la puerta está cerrada.

PAW tiene para su uso especifico varias banderas \(de la 0 a la 10 y de la 29 a la 59\). Por eso, si el valor que aparece al lado de la bandera 38 es igual a 0, PAW sabe que tu localidad actual es 0 en Para ver cómo funciona esto, teclea ENTER de nuevo \(con ENTER cambiamos el uso entre la opción diagnóstico o continuar con el INPUT si no has tecleado ningún otro comando\) y vámonos hacia el principio del juego usando la palabra NORTE o cualquier otra dirección que hayas puesto. De nuevo, antes de cualquier otra cosa teclea ENTER y verás que la bandera ha cambiado a 2, esto es, por supuesto, porque estás en la localidad 2.

```
Flag 38 = 2 ?
```

Puedes mirar a los valores de cualquier otra bandera tecleando su número antes de apretar el ENTER, por ejemplo: 100 ENTER y entonces puedes ver el valor de esa bandera.

```
Flag 100 = 0 ?
```

Pero hay otra opción mucho más potente que te deja poner el valor que quieres que tenga una bandera. Ello se hace poniendo el signo = frente al número. Por ejemplo, si en este momento tecleas = 10 ENTER verás que la bandera 100 se ha hecho = a 10.

```
Flag 100 = 10 ?
```

La bandera 100 no hace nada en este juego y su valor no es importante, pero si te pones a practicar por tu cuenta ten cuidado de NO cambiar los valores de ninguna otra bandera de momento, porque te puedes tropezar con alguna otra bandera que SI sea importante, y el juego se te haga un enredo. Vuelve a la línea de INPUT pulsando ENTER y veamos que más puede hacer PAW.

Ahora sí que seremos capaces de manipular los objetos en el juego. De momento la bolsa estará en la parada del autobús. Con nosotros llevaremos el emparedado, la manzana, una antorcha apagada, y el anorak puesto.

Usa el diagnóstico para ver el valor de la bandera 1 \(se hace con ENTER 1 ENTER\), y vemos que tiene el valor de 3, que es el número de objetos que se llevan en las manos, pero no puestos encima. Volvamos a la línea de INPUT y tecleemos "coger saco" y PAW imprimirá el mensaje "Ahora cojo el saco".

Es lo que se llama AUTO-REPORTING \(i posición del saco haya cambiado de la localidad 2 que era la parada del autobús a la localidad 254 \(que es una localidad especial para los objetos que puedan ser llevados pero no puestosnforme automático de cualquier acción que hayas hecho\).

Esta última orden ha hecho que la posición del saco haya cambiado de la localidad 2 que era la parada del autobús a la localidad 254 \(que es una localidad especial para los objetos que puedan ser llevados pero no puestos\).

Fíjate que no hay ningún cambio en la tabla donde se localizan los objetos al comienzo, sino que lo que ha cambiado es la copia que se ha hecho de la base de datos cuando se empieza el juego. Si ahora miras el valor de la bandera 1 \(fíjate también cómo cuando se selecciona diagnóstico estará en uso la última bandera que hayas mirado\) verás que su valor ha aumentado a 4.

Ahora prueba "quitar anorak" y recibirás el mensaje "No puedo quitarme el anorak, mis manos están llenas". Esto es porque PAW inicialmente \(si tú no has dicho lo contrario\) sólo permite al jugador llevar 4 objetos al mismo tiempo, y en algunos casos esta limitación puede impedirle al jugador quitarse vestido, etc., \(de hecho, quitarse una prenda es cambiar la posición de ese objeto de la localidad 253, que es llevado encima, a la localidad 254 que es llevado en la mano\).

Si, por ejemplo, dejamos el saco primero y tecleamos "quitar anorak" veremos que sí se puede. Si miras otra vez a la bandera 1 te darás cuenta de que todavía tiene el número 4, esto es porque al quitarte el anorak has aumentado el número de objetos que llevabas en tus manos.

Ahora, como prueba, teclea las siguientes órdenes y fíjate qué hace cada una \(usando las banderas\):

```
Coger Bolsa

Quitar Anorak

Poner Anorak

Coger Manzana

Coger Billete de autobús
```

Hay que darse cuenta de que todas las respuestas, excepto la de la última orden, mencionan los objetos por su nombre, esto es porque estaban todos a la vista y por lo tanto el jugador sabía que existían \(estaban en su propia localidad\). Pero para un jugador que no conociera el juego, el billete todavía no existiría, y si al teclear "coger billete" ya en la respuesta lo mencionamos por su nombre, le estamos dando una pista muy importante. Y es que el PAW es muy cuco.

Si tratas de poner cualquier cosa dentro del saco descubrirás que PAW lo que hace es dejar caer los objetos al suelo, esto es porque no le hemos dicho a PAW todavía qué cosas pueden ser puestas dentro de la Bolsa. Solamente le hemos dicho de momento que es un contenedor, en el próximo capitulo trataremos de este tema.

Finalmente encentraremos un terrible "error" en nuestro juego: si tecleamos "coger la puerta", se nos dará la respuesta de "No hay ninguna de esas aquí" o "No está eso aquí". No debería decir eso, porque en la descripción hemos dicho que hay una puerta.

Este es un problema muy frecuente, y ocurre porque le hemos dicho a PAW que hay una manzana, un emparedado, etc., pero no le hemos dicho que existe una puerta, y si usas coger o dejar, etc, con cualquier palabra que no esté en el vocabulario entonces PAW asume que es un objeto que "no está aquí". Sin embargo, una vez que esa palabra entre en el vocabulario, PAW sabrá que no es un objeto \(siempre que no haya una entrada para esa palabra en la tabla de relación-objeto-palabras\) y dará la respuesta "no puedo hacer eso" que es la correcta.

Así que volvamos al menú principal tecleando FIN, ENTER, SI, ENTER, NO, ENTER y seleccionaremos de nuevo la opción de Vocabulario V.

Pongamos todos los nombres de las cosas que hayamos usado en la descripción, aunque no sean objetos, tales como:

```
Puerta     57

Reja     58

Hierba     59

Camino     60

Banco     61

Estanque 62    

Árbol     63

Rama     63

Hoja     63
```

Es importante que árbol, rama y hoja reciban el mismo número, porque no intentamos que sean manipulables, sino que solamente las entienda el PARSER. Si fueran manipulables, tendríamos que darles números diferentes. Esto es una consideración importante de diseño.

Ahora puede ser el momento de hacer otro test del juego para ver que la orden "coger puerta" produzca una respuesta correcta.

De momento hemos creado las localidades, las hemos conectado entre sí, hemos creado y descrito los objetos, les hemos asignado una palabra desde el vocabulario, un punto de comienzo en el juego, un peso relativo, si eran llevables o quitables, y si eran contenedores. El próximo capitulo tratará de cómo se crean algunos problemas y otros personajes para hacer que el juego sea más interesante.

