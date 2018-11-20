# DEBUG

## BUGS

#### add_array_static

Faltaba include <stdlib.h> que contiene la función abs
la cual se utiliza en la función `add_array`

El for loop dentro de la función `add_array` tiene que ejecutarse mientras i "<" n, no mientras <= n + 1

### add_array_dynamic

El for loop dentro de la función `add_array` tiene el mismo problema que en `add_array_static`.

### add_array_segfault

también incluir <stdlib.h> para poder usar abs dentro de `add_array`
estaba haciendo dos punteros *a y *b que no apuntaban a nada, definí a "a" y "b" como dos arrays estáticos de tamaño 3.

## FLOATING POINT EXCEPTION

-DTRAPFPE genera la inclusion de las funciones
`set_fpe_x87_`
`set_fpe_x87_sse`
`clear_fpe_x87_sse`

para linkearlo correctamente:

`gcc -Ifpe_x87_sse -D TRAPFPE comparison.c fpe_x87_sse/fpe_x87_sse.c -lm -o comparison.e`

En los tres casos el tag agrega la función set_fpe_x87_sse la cual habilita el "trapping" de OVERFLOW, DIBVYZERO E INVALID
es decir, sin TRAPFPE puedo dividir por cero o realizar otras operaciones "invalidas" sin generar una excepcion.

### para "comparsion.c"
si quiero dividir por 0 normalmente se genera una floating point exception (esto es lo que sucede cuando utilizo el tag TRAPFPE), si lo compilo sin este tag e intento dividir por 0 el resultado de dicha división será "inf" (infinito) sobre el cual luego se podrá operar para realizar la comparación que este programa realiza.

### para "division.c"
si quiero dividir por 0 normalmente se genera una floating point exception (esto es lo que sucede cuando utilizo el tag TRAPFPE), si lo compilo sin este tag e intento dividir por 0 el resultado de dicha división será "inf" (infinito) 

### para "square_root.c"
si quiero hacer la raiz cuadrada de un numero negativo por ejemplo el resultado normal es una floating point exception, esto es lo que sucede utilizando el tag TRAPFPE. si lo compilo sin este tag el resultado de tratar de calcular la raiz cuadrada de un número negativo sera un NaN

## SEGMENTATION FAULT

..* small no produce ningún error al compilar ni al correr

..* big se compila sin problemas pero al momento de correrlo genera una "Segmentation fault"

luego de ejecutar `ulimit -s unlimited`  big deja de generar la segmentation fault (pero tuve que cancelarlo porque me estaba explotando la máquina virtual, jaja).

con unlimit -s le saco el límite al stack size, es decir permito que se utilice más memoria que la establecida por default, esto sería una solución grosera, no de debuggeo y debería ser utilizada con precaución.

para solucionar esto podría cambiar los tipos de A y C, en lugar de floats que fueran doubles o long doubles.

## VALGRIND
..* En el caso de test_oob4 tiene 2 errores con leak de memoria.
..* No pude trabajar con source1.c por un problema de mi maquina virtual.

## FUNNY
..* Cuando se compila sin el flag se genera una segmentation fault

..* Cuando se compila con el flag DEBUG se imprime un mensaje ('I'm HERE !!!!) pero igualmente se produce una segmentation fault.

las diferencias estan dadas por que el mensaje de error (i'm here) solo se genera e imprime si se compila con el tag DEBUG









	
