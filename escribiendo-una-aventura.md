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

