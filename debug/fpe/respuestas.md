-DTRAPFPE genera la inclusion de las funciones
set_fpe_x87_
set_fpe_x87_sse
clear_fpe_x87_sse !!!###

para que linkearlo correctamente:

gcc -Ifpe_x87_sse -D TRAPFPE comparison.c fpe_x87_sse/fpe_x87_sse.c -lm -o comparison.e

En los tres casos el tag agrega la función set_fpe_x87_sse la cual habilita el "trapping" de OVERFLOW, DIBVYZERO E INVALID
es decir, sin TRAPFPE puedo dividir por cero o realizar otras operaciones "invalidas" sin generar una excepcion.

## para "comparison.c"
si quiero dividir por 0 normalmente se genera una floating point exception (esto es lo que sucede cuando utilizo el tag TRAPFPE), si lo compilo sin este tag e intento dividir por 0 el resultado de dicha división será "inf" (infinito) sobre el cual luego se podrá operar para realizar la comparación que este programa realiza.

## para "division.c"
si quiero dividir por 0 normalmente se genera una floating point exception (esto es lo que sucede cuando utilizo el tag TRAPFPE), si lo compilo sin este tag e intento dividir por 0 el resultado de dicha división será "inf" (infinito) 

## para "square_root.c"
si quiero hacer la raiz cuadrada de un numero negativo por ejemplo el resultado normal es una floating point exception, esto es lo que sucede utilizando el tag TRAPFPE. si lo compilo sin este tag el resultado de tratar de calcular la raiz cuadrada de un número negativo sera un NaN

