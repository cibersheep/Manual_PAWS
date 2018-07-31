## Editor de caracteres

Vamos a echar un vistazo rápido al editor de caracteres. Para ello, selecciona la opción \[Q\] del menú principal (los usuarios de 48K tendrán que cargar un _overlay_). Este submenú te permite cambiar la forma de los caracteres que se muestran en la pantalla. Se pueden tener hasta cinco sets de caracteres diferentes en memoria y en cualquier momento cambiarlos entre ellos usando `ESCC 0-5` o una acción «CHARSET» en la tabla de procesos o respuestas. Los sets de caracteres están numerados de 0 a 5. El set 0 es el set normal y no se puede cambiar a excepción de por los caracteres que tengan valores de 0 a 15, \(que son los diferentes patrones de sombreado\), y los que tengan del 144 al 185 \(que son los _gráficos definidos por el usuario,_ normales del Spectrum\). Si usas en este momento \[P\] para mirar la tabla, se mostrarán solamente estos caracteres. Tendrás que insertar un set en blanco antes de que lo puedas cambiar o cargar. Esto se hace para conservar memoria en la base de datos si no vas a cambiar los sets de caracteres.

De momento, solamente vamos a usar el editor para cambiar una de los patrones de sombreado. Estos son solamente caracteres normales con los cuales el sistema gráfico colorea un área de la pantalla.

\[A 0 15 ENTER\] permitirá que edites el carácter 15 del set 0. Como este es un sombreado poco importante, lo alteraremos para que represente el trabajo de la reja de hierro del pabellón de música.

###### Diagrama 5 ![1530652305542](/assets/diagrama05.png) {#diagrama05}

Cada caracter de PAW está definido por un entramado de 8 por 8 píxeles. La parte izquierda superior de la pantalla mostrará una versión aumentada del diseño tal y como está en este momento. En las cajas superior central y derecha se te mostrará cómo se ve cuando se use como un sombreado \(de ambas formas: la normal y la inversa\), mientras que la parte inferior de la pantalla se muestra un sumario de las órdenes a tu disposición y el set de caracteres que se está editando actualmente. Usa las teclas del cursor \(CAPS SHIFT 5 hasta 8 en un 48K\) para mover el cursor rojo parpadeante alrededor del entramado, y la tecla de espacio para cambiar el estado de un píxel. Es decir, si el píxel está encendido (negro) lo apagará; y si está apagado (amarillo o blanco) lo encenderá. Inténtalo y verás lo que queremos decir.

El sombreado o el diseño que requerimos es el que muestra el [diagrama 5](#diagrama05). Cuando hayas terminado usa \[R\] para que se redibujen los dos cuadros donde se muestran las cajas de sombreado y verás la nueva forma de entramado. Finalmente pulsa \[ENTER\] para terminar la edición.

La cara B de la cinta contiene 22 sets de caracteres diferentes que pueden ser cargados en los sets de caracteres del 1 al 5, después de haberlos insertado, por supuesto. Después de la inserción de un set, en el menú de colores de fondo, se ofrece la opción de usarlo como set principal o set por defecto.

