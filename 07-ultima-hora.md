## Notas adicionales para la última versión del PAW

La versión Castellana de PAW se corresponde con la versión A18 inglesa, siendo por lo tanto la más avanzada de las existentes.

Las diferencias con respecto a todo lo que se ha explicado en estos densos y sapientísimos manuales son:

### OVERLAYS PARA EL USUARIO

La última versión de PAW tiene una característica muy importante que permite, y de hecho facilita, la incorporación dentro del sistema de cualquier rutina o utilidad hecha por separado: son los overlays del usuario.

Estos añadidos deben estar escritos en Assembler y pueden tener hasta 5 K de longitud. Para ellos se ha añadido en el menú principal la opción Z, que te pregunta el nombre de la base de datos a cargar.

Puedes elegir entre cualquier letra (A - Z) y PAW empezará a buscar en el "periférico escogido" por una base de datos con esa extensión.

**PERIFERICO ESCOGIDO
(Current Device)**

PAW ahora te preguntará siempre en qué periférico vas a Salvar/Cargar tu base de datos. Puedes hacerlo en Disco, Cassette o Microdrive.

**DRIVERS DE IMPRESORAS**

El Driver de Impresora queda ahora limitado a 48 bytes en la dirección 29587 (PRTADD). Aunque la memoria ha quedado sensiblemente reducida, se ha hecho para poder dar más facilidades extras.

**EL PARSER**

En ésta versión se han hecho algunos sutiles cambios en la cadena que maneja el PARSER. Casi todos están encaminados a facilitar e implementar el manejo de los PSI. Pero, aunque no los uses, debes saber que existen, pues pueden afectar algunas partes del juego.

1. El condacto PARSE, mantiene ahora la «posición actual» dentro de una cadena en la SL que está siendo usada.
  Por lo tanto, un segundo condacto PARSE, continuará a partir de esa posición. En las versienes anteriores, un segundo condacto PARSE, hubiera dado como respuesta la misma SL que el primero.
  Por lo tanto la frase... Dile al Archivero "coge la espada y mata al dragón" es aceptada y ejecutada en cada una de sus acciones.

2. La acción PARSE, no afectará al indicador que marca si la "línea de comando" está vacía o llena, que estaba controlado por la acción NEWTEXT.
  Esto significa que una orden del tipo... Decir al Archivero "Coge la llave", ir al Norte, será en esta versión ejecutada correctamente, es decir, primero lo que has dicho al PSI y luego tu acción de irte al Norte.
  En versiones anteriores, el marcador controlado por NEWTEXT se hubiera seteado automáticamente, pero esto se ha cambiado para permitir, en caso de que haya múltiples acciones PARSE, encontrar el último comando de una cadena sin que la bandera se setee.
  Por lo tanto, en todos tus juegos previos debes añadir una acción NEWTEXT justo después de una orden PARSE (que es el exacto lugar donde el Proceso irá si no encuentra una sentencia válida en la cadena), si quieres mantener la compatibilidad.

3. El Verbo y Adverbio actuales no se borran (las banderas 33 y 36 permanecen seteadas) cuando se ejecuta la acción PARSE en una cadena. Esto significa, que si un Verbo (o un Nombre Convertible en verbo), es emitido de la primera frase en la cadena, el Verbo usado será el de la frase que inició o disparó la acción PARSE usualmente un... Decir a...)
  Esto es un cambio menor, pero significa que el Verbo Actual se contiene cuando la cadena sufre un PARSEado múltiple.

### UNA BANDERA MÁS

¿Recuerdas que te insistíamos mucho en que respetaras las banderas hasta la 60, porque se usarían en futuras expansiones?

Pues el caso ha llegado con esta nueva versión.

Nos congratulamos en anunciar que la bandera 58 ha alcanzado el estatus de "Bandera del Sistema". Si la seteas a 128 (es decir, el bit 7), PAW empezará a buscar pareja para palabras en una tabla de Procesos, cosa que antes, como recordaréis, sólo hacia en la tabla de Respuestas.

Esto facilita lo visto anteriormente en los PARSE múltiples, permitiendo acciones para un PSI en la tabla de Procesos 2. Estamos seguros, de que con tu habilidad habitual, le encontrarás otros usos. Pero este efecto se cancela la próxima vez que Proceso 1 y Proceso 2 sean ejecutados, porque PAW le resta a la bandera los 128 que le debía.

Esto es para asegurar que los Procesos 1 y 2 actúen con normalidad hasta que se les ordene de una manera especifica (con la bandera 58 en 128) que se comporten especialmente.

Suponemos que deducirás hábilmente que si pones 58 a 0, el efecto se anula.

A medida que vayamos introduciendo mejoras recibirás pronta documentación sobre ellas.

