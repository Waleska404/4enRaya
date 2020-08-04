# Cuatro en raya

Proyecto en haskell para la asignatura Lenguajes de Programación.



### Prerequisitos 📋

Es necesario instalar ghc para compilar el programa.

```
sudo apt install ghc
```

### Instalación 🔧

Primero se compila, generando el ejecutable.

```
ghc joc.hs
```

Después ejecutar.

```
./joc
```

## Instrucciones

Una vez ejecutado el archivo, es necesario escoger una serie de parámetros antes de empezar a jugar.

### Estrategia:

Lo primero que veremos al ejecutar es el título, y una línea que nos pide indicar con que estrategia queremos que juegue el ordenador.

```sh
> 4 EN RAYA
> Escoge la estrategia que seguira el ordenador: (Smart/Greedy/Random)
```

Se indicara escribiendo una de las tres opciones propuestas y presionando 'enter'.
Es importante escribir exactamente una de las tres opciones propuestas (incluyendo la mayúscula inicial).

Por ejemplo:

```sh
> 4 EN RAYA
> Escoge la estrategia que seguira el ordenador: (Smart/Greedy/Random)
> Greedy
```


### Tamaño del tablero

Para continuar hay que especificar el tamaño del tablero con el que se quiere jugar.
Primero preguntara cuantas filas queremos en el tablero y después las columnas. Hay que indicar el número en cada caso y presionar 'enter'.

Por ejemplo:

```sh
> Escoge las filas del tablero:
> 5
> Escoge las columnas del tablero:
> 5
```

### ¿Quién tira primero?

Por último se muestra el tablero y se pregunta si es el jugador humano quien tira primero o el ordenador:

```sh
> | | | | | |
> -----------
> | | | | | |
> -----------
> | | | | | |
> -----------
> | | | | | |
> -----------
> | | | | | |
> Tiras primero? (s/n) 
```
Si se quiere tirar primero indicar con una 's' y presionar 'enter', en caso contrario indicar con una 'n'.

Por ejemplo:

```sh
> Tiras primero? (s/n) 
> s
```
El jugador que tira primero sera el jugador 'X', las casillas en las que tire serán marcadas con una 'X'. El otro jugador sera el 'Y' y sus casillas quedarán marcadas con una 'Y'.

En este ejemplo se muestra el tablero después de un turno cada jugador:
```sh
> | | | | | |
> -----------
> | | | | | |
> -----------
> | | | | | |
> -----------
> | | | | | |
> -----------
> |Y| | | |X|
```


### Durante el juego

Una vez decidido quien tira primero el juego comienza. Cuando sea el turno del ordenador se mostrará el tablero añadiendo su tirada:
``` sh
Movimiento ordenador:
> | | | | | |
> -----------
> | | | | | |
> -----------
> | | | | | |
> -----------
> | | | | | |
> -----------
> |Y| | | | |
```

Cuando sea el turno del jugador humano se le preguntara en que columna quiere colocar su próxima ficha.

```
> En que columna colocas ficha? (de 1 al numero de columnas): 
```

La columna se debe indicar escribiendo el número correspondiente a la columna, desde el 1 hasta el número de columnas que se hayan escogido, y presionando 'enter'.
La ficha se colocara en la columna escogida en la fila más baja posible.
Por ejemplo:

```sh
> En que columna colocas ficha? (de 1 al numero de columnas): 
> 5
> | | | | | |
> -----------
> | | | | | |
> -----------
> | | | | | |
> -----------
> | | | | | |
> -----------
> | | | | |X|
```


### Finalización

El juego acaba cuando uno de los dos jugadores consigue alinear cuatro fichas en horizontal, vertical o diagonal. Es posible el empate en caso de que el tablero se complete sin que ningún jugador tenga cuatro fichas en línea.

Ejemplo de empate:
```sh
> |Y|Y|X|X|X|
> -----------
> |Y|X|Y|Y|X|
> -----------
> |Y|Y|X|Y|Y|
> -----------
> |X|X|X|Y|X|
> -----------
> |Y|X|X|X|Y|
> Empate
```

Ejemplo en caso que de que gane el ordenador:
```sh
Movimiento ordenador:
|Y|X| | | |
-----------
|Y|Y| | | |
-----------
|Y|X|X| | |
-----------
|Y|X|X|Y| |
-----------
|X|X|X|Y|Y|
Gana ordenador
```

Ejemplo en caso que de que gane la persona:

```sh
En que columna colocas ficha? (de 1 al numero de columnas): 
2
| | | | | |
-----------
| |X| | | |
-----------
| |X| | | |
-----------
|Y|X|Y| |Y|
-----------
|Y|X|X|X|Y|
Gana persona
```


## Descripción de las estrategias

### Random
En el caso de la estrategia random cada tirada del ordenador es una columna al azar.



### Greedy
La estrategia greedy consiste en conseguir el máximo de fichas en linea en cada tirada. Y que en caso de que sea posible evita el cuatro en raya del contrincante.

### Smart
La estrategia smart decide el mejor movimiento posible haciendo una búsqueda en profundidad. Para implementar esta estrategia he utilizado el algoritmo minimax.

Dado que trabaja con una profundidad de búsqueda determinada, esta se puede cambiar, y cuanto más alta sea mas competitivo sera el ordenador, pero también tardara más en hacer un movimiento.
El tiempo de ejecución en esta estrategia también varía según el tamaño del tablero.
Lo he dejado en una profundidad = 6 pero este parámetro se puede modificar como muestro a continuación.  

En la línea 44 del archivo joc.hs se indica la profundidad que se utiliza. Ese numero es el que se tiene que cambiar en caso de querer que el algoritmo minimax trabajo con otras profundidas.
Si se cambia este parametro es necesario guardar el archivo y volver a compilarlo (como se indica en el paso Instalación de este Readme).

```sh
42 --definir y poder cambiar la profundidad de busqueda del algoritmo minimax en la estrategia smart
43 profundidadDeBusqueda :: Int
44 profundidadDeBusqueda = 6
```


## Autora
Paula Boyano Ivars
