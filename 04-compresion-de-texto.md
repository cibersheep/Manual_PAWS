## COMPRESION DE TEXTO

La opción K del menú principal \(los usuarios de 48K tendrán que cargar un overlay en este punto\) preguntará si quieres comprimir la base de datos, cualquier tecla que teclees aparte de la S de "sí" te mandará de vuelta al menú principal.

El compresor de texto reducirá la cantidad de memoria que se necesita para el texto de tu juego agrupando las letras más comunes en "tokens". Esto puede tomar desde un minuto hasta una hora dependiendo del tamaño de tu juego. En este juego de demostración que estamos haciendo llevará más o menos un minuto y salvará unos 900 bytes.

La única diferencia que encontrarás es que, cuando estás editando un texto que ya existe, el cursor pegará saltos de dos, tres, y a veces cuatro y cinco caracteres de una sola vez. Lo mismo pasará al borrar. Si se hace alguna corrección hay que teclear todas las letras separadas, puesto que ya serán comprimidas la próxima vez que uses el compresor. Es de notar que el compresor usa los tokens normales del Spectrum, lo que producirá agrupaciones de letras, pero no de las palabras claves después de que uses el compresor.

Muy importante es que no uses los tokens, o sea, las palabras clave, si luego vas a comprimir la base de datos, \(es decir, no pongas tokens dentro de tu texto si después vas a comprimir\). Y para saber lo que son tokens mira el manual de tu ordenador.

