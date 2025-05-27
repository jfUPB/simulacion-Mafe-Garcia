#### Paso por valor y paso por referencia:

En las lineas:

``` js
let friction = this.velocity.copy();
let friction = this.velocity;

```

La que tiene copy(), es una linea donde velocidad pasa por valor, mientras que la otra pasa por referencia, cuando pasa por referencia esto puede afectar el valor inicialmente indicado de velocity, mientras que el que tiene copy, saca una copia, solo afecta fricción.

