# CSS

## Especificidad en CSS

Para saber qué regla gana cuando dos chocan, el navegador le da puntos a cada selector:

- Etiqueta (a, p, h2): 1 punto
- Clase (.btn-comprar): 10 puntos
- ID (#btn-destacado): 100 puntos

Por ejemplo, `header nav ul li a` suma 5 puntos porque tiene 5 etiquetas, y `.btn-comprar` suma 10 porque es una clase.

En el ejercicio le puse al botón del primer producto una clase y un ID, cada uno con un color distinto. Aunque la regla del ID estaba antes en el CSS, el botón se vio con el color del ID, porque 100 puntos le ganan a 10.

Para arreglarlo quité las reglas con ID y usé solo clases (`.btn-comprar` y `.btn-destacado`). Como ahora las dos valen 10 puntos, gana la que está más abajo en el archivo, y así no tuve que usar `!important`.

## Hallazgos: El Modelo de Caja

La diferencia practica entre Margin y Padding.

-El padding es el espacio dentro de la caja, entre el contenido y el borde, y el fondo del elemento sí lo cubre. 

-El margin es el espacio fuera de la caja, entre ella y las demás, y siempre es transparente.

## 2. Por qué es obligatorio usar box-sizing: border-box

Por defecto el navegador suma padding y borde al ancho declarado. 

Un elemento de width: 300px con padding: 20px termina midiendo 340px y puede desbordar a su contenedor padre. 

Con border-box el padding y el borde se cuentan dentro de los 300px, así que el elemento crece hacia adentro y no rompe el diseño.

## 3. Cómo se ven afectados los elementos hermanos cuando le aplicas un margen grande a uno de ellos.

Margen grande en un elemento hermano: el elemento con margen grande empuja a sus hermanos y se aleja de ellos.

Con ese cambio los vecinos se desplazan, y el espacio entre los dos aumenta.

## ## Hallazgos: Centralización de Identidad Visual y Espaciado

### 1. Variables declaradas en `:root`

**Colores**
- `--color-primario: #f4c1ef;`
- `--color-secundario: #914506;`
- `--color-fondo: #f89a97;`
- `--color-texto: #ffffff;`


**Tipografía**
- `--fuente-principal` (Saira, importada desde Google Fonts)

**Espaciados**
- `--espaciado-pequeno` (8px), 
- `--espaciado-medio` (15px), 
- `--espaciado-grande` (20px)

### 2. Ventaja de reutilizar medidas de margen y relleno

Es mejor usar las mismas medidas de espacio en toda la página
en lugar de inventar un número nuevo en cada parte. Así todas las tarjetas
y secciones se ven ordenadas y con el mismo "aire". Además, si quiero
cambiar el espacio, solo lo cambio en un lugar y se actualiza todo, sin
tener que buscar uno por uno.

### 3. Cómo `:root` previene colisiones visuales

Cuando la hoja de estilos crece, es fácil que dos selectores terminen con
tonos "casi iguales" o medidas ligeramente distintas. Al tener una única
fuente de verdad en `:root`, cada color y medida tiene un nombre y un solo
lugar donde se define, lo que evita inconsistencias, duplicados y errores
al agregar nuevos componentes.

## Hallazgos: Pseudoclases y Pseudoelementos

### 1. Pseudoclase vs. pseudoelemento

Una pseudoclase (`:hover`, `:focus`, `:active`) cambia el estilo de un elemento
que ya existe cuando el usuario interactúa con él. Un pseudoelemento
(`::before`, `::after`) no reacciona a eventos, sino que inyecta contenido
nuevo que no está en el HTML, como el punto del menú o la insignia "¡Oferta!".

### 2. Importancia de :focus en la accesibilidad

Quienes navegan con la tecla Tab necesitan ver en qué enlace o botón están
ubicados. `:focus` con un contorno visible lo permite, y quitarlo hace la
página difícil de usar, por lo que es una buena práctica de accesibilidad.

### 3. Decoración con ::before/::after en lugar de HTML

Poner iconos o etiquetas desde CSS mantiene el HTML limpio, sin etiquetas
vacías, y permite cambiar el diseño en un solo lugar sin editar cada tarjeta.