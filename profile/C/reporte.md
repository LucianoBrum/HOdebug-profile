## Para profile_me_1.c (ejemplo):

### Sin ningún tag de optimización durante compilación.

 Midiendo por time:	
	real	0m9,381s
	user	0m5,905s
	sys	0m0,763s

* Midiendo por gprof

  %   cumulative   self              self     total           
 time   seconds   seconds    calls  ns/call  ns/call  name    
 83.91      4.19     4.19 25000000   167.48   167.48  first_assign
 12.86      4.83     0.64                             main
  3.52      5.00     0.18 25000000     7.02     7.02  second_assign

### Optimizando con -O0

midiendo por time:
	real	0m5,982s
	user	0m4,438s
	sys	0m0,414s

 * EL TIEMPO REAL SE REDUCE CASI A LA MITAD

* Midiendo por gprof los tiempos no se reducen tanto, sobre todo en main.

### Optimizando con -O1

midiendo por time:
	real	0m5,013s
	user	0m3,882s
	sys	0m0,417s
 
* NO SE REDUCE TANTO EL TIEMPO REAL, PERO SI EL DE USER. EL TIEMPO DE SYSTEM AUMENTA LIGERAMENTE CON RESPECTO A OPTIMIZAR CON O0

* Midiendo por gprof, se reducen los tiempos en los dos assigns y en main.

### Optimizando con -O3 (no hice O2 por que el tipo de optimización es similar)

Los tiempos de ejecución a "simple vista" son notablemente más cortos

Midiendo por time:
	real	0m0,001s
	user	0m0,001s
	sys	0m0,000s

 * TODOS LOS TIEMPOS SE VEN DRÁSTICAMENTE DISMINUIDOS. ESTO DEBERÍA SER A COSTA DE UN MAYOR TIEMPO DE COMPILACIÓN, PERO EN ESTE CASO COMO ESTE ES UN CODIGO "CHICO" ESTE COSTO NO SE NOTA.

* Midiendo por gprof: no se puede llegar a medir ni siquiera porque los tiempos son menores al tiempo de sampleado!
