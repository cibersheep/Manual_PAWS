## Uso de los «overlays»

Un usuario de un 128K probablemente no necesitará el uso de la paginación todavía pero puede encontrar útil este capítulo.

Ya explicamos en la sección [conceptos](01-conceptos.md#paginacion-de-memoria) el concepto de la paginación. Para poder procesar los gráficos y la compresión del texto, por ejemplo, un usuario de 48K tendrá que cargar un _overlay_ o página aparte.

PAW hará casi todo el trabajo por ti. Si seleccionas la opción de menú que necesitas, se te pedirá que confirmes si quieres cargar o no un _overlay._ Pulsando cualquier tecla que no sea la «S» o la «Y» \(de _yes_\) te mandará al menú principal. Si continúas, PAW imprimirá en la pantalla el nombre del _overlay_ que está buscando.

Los cinco archivos de _overlays_ se encuentran al final del programa principal, que es donde la cinta quedará situada después de cargar el PAW. Si tienes un contador de revoluciones, es importante que lo pongas a cero en este punto, hagas una lectura de dónde comienza cada _overlay_ y así puedas ir directamente a cada uno de ellos. Los cinco _overlays_ están en el orden que mostramos más abajo. También se describiben las opciones que contiene cada uno \(ten en cuenta que la selección de una opción presente en el _overlay_ actual es automática\):

| Overlay | Nº | Descripción |
| :--- | :---: | :--- |
| PAWOVR | 1 | Intérprete, juego de prueba, grabar y comprobar aventura. |
| PAWOVR | 4 | Tablas de procesos y respuestas, vocabulario, conexiones y palabras. |
| PAWOVR | 5 | Mensajes, localidades, objetos, peso de objetos, lugar inicial y colores de fondo. |
| PAWOVR | 2 | Compresor. |
| PAWOVR | 3 | Editor de caracteres y el editor gráfico. |

Nota: Grabar, verificar y cargar una base de datos, junto con la memoria libre, están siempre a tu disposición, puesto que son parte del menú principal.

Una vez que se ha cargado una base de datos, se te presentará un menú como siempre. Si ocurre algún error puedes regresar al menú principal, volver a seleccionar la opción y probar de nuevo. Es importante que tengas en cuenta que cualquier _overlay_ cargado previamente se borrará si ocurre un error de carga, por lo que, a menos que tengas suficiente memoria para mantener los _overlays_ principales, no podrás hacer nada excepto cargar un nuevo _overlay_ o hacer un _save_ \(grabar\) o un _load_ \(cargar\) de la base de datos, que siempre está disponible.

Si no tienes un contador de revoluciones o quieres hacer las cosas más sencillas, se puede pasar cada una de las bases de datos a una cinta aparte. Son bases de datos de tipo CODE.


