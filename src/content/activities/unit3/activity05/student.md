#### Problema de planteamiento:

Se plantea que para que la aceleraciónd e el mover dependa de las fuerzas que actuan sobre el, se debe poner

``` js
mover.applyForce(wind);
```

``` js
mover.applyForce(gravity);
```

Y en el metodo applyForce:

``` js
applyForce(force) {
  this.acceleration = force;
}
```


Considero que este planteamientos no funciona por varias razones:

1. No se estan sumando las fuerzas si no aplicando una tras de la otra.
2. En el metodo applyForce solo se iguala la fuerza a la aceleración que ya existe, es decir que no varia.
