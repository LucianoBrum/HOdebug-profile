### DEBUG

## BUGS

#add_array_static
 Faltaba include <stdlib.h> que contiene la función abs
la cual se utiliza en la función add_array

El for loop dentro de la función add_array tiene que ejecutarse mientras i "<" n, no mientras <= n + 1

#add_array_dynamic
El for loop dentro de la función add_array tiene el mismo problema que en add_array_static.

#add_array_segfault
también incluir <stdlib.h> para poder usar abs dentro de add_array
estaba haciendo dos punteros *a y *b que no apuntaban a nada, definí a "a" y "b" como dos arrays estáticos de tamaño 3.





	
