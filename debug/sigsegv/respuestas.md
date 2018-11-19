..* small no produce ningún error al compilar ni al correr

..* big se compila sin problemas pero al momento de correrlo genera una "Segmentation fault"

luego de ejecutar `ulimit -s unlimited`  big deja de generar la segmentation fault (pero tuve que cancelarlo porque me estaba explotando la máquina virtual, jaja).

con unlimit -s le saco el límite al stack size, es decir permito que se utilice más memoria que la establecida por default, esto sería una solución grosera, no de debuggeo y debería ser utilizada con precaución.

para solucionar esto podría cambiar los tipos de A y C, en lugar de floats que fueran doubles o long doubles.
