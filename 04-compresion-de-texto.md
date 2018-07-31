## COMPRESION DE TEXTO

La opción \[K\] del menú principal \(los usuarios de 48K tendrán que cargar un _overlay_ en este punto\) te preguntará si quieres comprimir la base de datos, cualquier tecla que pulses aparte de la «S» de «sí» te mandará de vuelta al menú principal.

El compresor de texto reducirá la cantidad de memoria que se necesita para el texto de tu juego agrupando las letras más comunes en _tokens_ \(«símbolo» en inglés. N. del E.\). Esto puede tomar desde un minuto hasta una hora dependiendo del tamaño de tu juego. Para el juego de demostración que estamos haciendo debería tomar más o menos un minuto y ahorrará unos 900 bytes.

La única diferencia que encontrarás es que, cuando estás editando un texto que ya existe, el cursor pegará saltos de dos, tres, cuatro e incluso, cinco caracteres de una sola vez. Lo mismo pasará al borrar. Si se hace alguna corrección que requiera su borrado, tendrás que teclear todas las letras separadas y serán comprimidas la próxima vez que uses el compresor. Ten en cuenta que el compresor usa los _tokens_ normales del Spectrum, lo que producirá agrupaciones de letras, pero no de las palabras claves después de que uses el compresor. Es muy importante que no uses los _tokens,_ o sea, las palabras clave, si luego vas a comprimir la base de datos, \(es decir, no pongas _tokens_ dentro de tu texto si después vas a comprimir\). 

Para saber más acerca de lo que son _tokens,_ mira el manual de tu ordenador.

