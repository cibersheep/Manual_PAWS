## Conceptos

Es una buena idea introducir algunos conceptos importantes utilizados por PAW.

### Secciones de datos

Durante muchos años ha sido de práctica común en los ordenadores que utilizan disco como soporte principal, el partir los programas largos en dos o más secciones que se cargan desde el disco cuando se van a utilizar. Este sistema no ha sido muy utilizado en cintas por su misma naturaleza como contenedor de datos en forma seriada.

PAW usa una forma muy simple para dejar el máximo de memoria libre, tanto en 48K como en 128K. Utiliza la memoria disponible para ir guardando porciones de datos hasta el momento en que esa memoria va siendo usada y sobreescrita. Los datos entonces se van obteniendo desde cinta según se requieran.

En un 128K no hay necesidad de preocuparse por las secciones de datos hasta que las últimas 16K son usadas \(es decir, hasta que se lleva escrita una aventura ¡de cerca de 92K!\).

En 48K las secciones se empezarán a necesitar en el momento de usar los gráficos o al llevar escritas ya 16K de programa.

La muestra en este manual no necesita secciones extra de datos así que su uso se explicará en detalle más adelante.

### Paginación de memoria

El 128K usa un sistema llamado paginación para obtener su memoria extra; el [diagrama 1](#diagrama01) ayudará a visualizar su composición. En él se ve que la parte superior se puede mover como una diapositiva en un proyector para que cada una de las páginas de 16K se pueda acomodar en un ordenador que solo puede ver 64K cada vez \(ver [diagrama 1](#diagrama01)\).

###### DIAGRAMA 1![](/assets/diagrama01.png) {#diagrama01}

**Nota:** las páginas 2 y 5 son el área de memoria donde se localiza el PAW y por ello no están disponibles. La zona de memoria marcada como secciones de datos será usada por PAW si es necesario \(ver [sección anterior](#paginación-de-memoria)\).

### Base de datos \(BD\)

PAW guarda el juego en una base de datos \(una colección de tablas e información que definen el juego que se está escribiendo\). Inicialmente la BD es muy pequeña y sólo contiene las palabras y órdenes más comunes en estos juegos.

Esta base de datos va poco a poco usando el área de memoria que se muestra como libre en el [diagrama 1](#diagrama01).

PAW también puede hacer uso de otras páginas, pero en un 48K esas páginas extra no están disponibles. Lo que significa que si se usa un 128K para escribir la aventura y se quiere que ésta corra tanto en 128 como en 48K, no se debe usar otra página sino la principal \(la 0\).

### Parser

> _To Parse:_ clasificar una palabra o analizar una frase en sus términos gramaticales.

PAW convierte lo tecleado por el jugador en series de sentencias lógicas \(SLJ\) para las cuales ya hay una respuesta definida. Esto se hace extrayendo frases de la cadena de input, de una en una y dejando que el intérprete las descifre. Las frases pueden ir separadas por cualquier signo de puntuación y por las conjunciones y, entonces, o luego \(o la que se haya definido\). Cuando ya no hay mas frases en la actual cadena de input, se pide otra al jugador. Una frase debe consistir al menos en un verbo \(indica acción\); opcionalmente dos nombres \(objetos o personajes\); posiblemente asociados a adjetivos \(que los describen\); de adverbios \(que modifican al verbo\); de una preposición \(que muestra la relación de un nombre con otra palabra\); y también puede contener una "cadena entre comillas para hablar con otros personajes".

### Menú

Del menú principal, mostrado al pulsar cualquier tecla desde la página de titulo, se puede acceder a cualquier opción del PAW con sólo teclear una sola letra \(en MAYUSCULAS\) seguido de ENTER.

El menú está dividido en dos partes y la opción E permite cambios entre ellas. La parte inicial muestra todas las funciones necesarias para crear un juego. La segunda \(accesible con E\), contiene todo lo necesario para Salvar, Cargar, Verificar, Probar el juego, etc. y también el diseñador de caracteres y el compresor de textos \(se explicarán más adelante\).

Si te encuentras con la pregunta: ¿carga de sección de datos?, es porque la parte a usar no está presente en ese momento y requiere que se cargue de memoria externa \(ver secciones de datos\). Entonces se requerirá teclear sí o no, ENTER. En el momento actual no la necesitaremos = no, ENTER.

### Línea de edición

Similar a la de input en Basic; se pueden usar las teclas de cursor para moverse a derecha e izquierda y DELETE para borrar lo que está a la izquierda del cursor. EDIT debe ser tecleado dos veces, o apretado hasta que se auto repita para limpiar cualquier cosa que se haya tecleado.

CURSOR Y ABAJO \(6\) debe ser tecleado dos veces o apretado hasta que se repita para abandonar el texto presente, la diferencia es que aquí se deja el texto que se estaba escribiendo en la base de datos y con EDIT se borra todo.

### Memoria libre

Con F se muestra la memoria disponible en cada página. En 48K se referirá sólo a la página 0. Además, se muestran también la localidad y el mensaje más alto usados hasta el momento. La razón de esta información tan útil se explica más adelante. Apretando cualquier tecla se vuelve al menú.

### Salvando, cargando y verificando la base de datos

Como es obvio que no se puede terminar un juego de una sola sentada y existe el peligro de pérdida de información por cualquier fallo del sistema, estas opciones permiten pasar a cinta o a disco un fichero con toda la información.

Con S se pedirá un nombre de fichero, te sugerimos ponerle un nombre que sea significativo y que contenga el número de la versión o la fecha.

La BD se salvará en varias partes. PAW salva dos ficheros por página, cambiando la última letra del nombre a A, B, C, etc para cada uno usado.

Con H se verificará la BD salvada comparándola con la que hay en memoria. Si se detecta un error, entonces hay que volver a salvar la BD en una cinta diferente si es necesario.

Con J se pide el nombre de la BD que se desee cargar de nuevo dentro de PAW. Cualquier base de datos que esté presente dentro de PAW se borrará para dejar paso a la nueva.

Si se produce un error de carga, se corromperá toda el área donde se aloja la BD y la única opción que se debe hacer es continuar con J hasta que la BD se haya cargado satisfactoriamente. Cualquier otra opción producirá daño al programa propio de PAW y se necesitará una recarga completa.

**Regla:** salva tu base de datos regularmente y en cintas diferentes para tener así un resguardo en caso de producirse el clásico corte de luz u otro accidente cualquiera.

