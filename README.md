# CSS

## Especificidad en CSS

Para saber qué regla gana cuando dos chocan, el navegador le da puntos a cada selector:

- Etiqueta (a, p, h2): 1 punto
- Clase (.btn-comprar): 10 puntos
- ID (#btn-destacado): 100 puntos

Por ejemplo, `header nav ul li a` suma 5 puntos porque tiene 5 etiquetas, y `.btn-comprar` suma 10 porque es una clase.

En el ejercicio le puse al botón del primer producto una clase y un ID, cada uno con un color distinto. Aunque la regla del ID estaba antes en el CSS, el botón se vio con el color del ID, porque 100 puntos le ganan a 10.

Para arreglarlo quité las reglas con ID y usé solo clases (`.btn-comprar` y `.btn-destacado`). Como ahora las dos valen 10 puntos, gana la que está más abajo en el archivo, y así no tuve que usar `!important`.
