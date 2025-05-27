#### Problema de planteamiento:

Como el objeto pasa por referencia, el valor de este siempre cambia sin importar donde se haga el cambio, es decir, el proximo frame la fuerza no sera su valor original si no que sera el valor de la ultima operacion en la que se uso, si por ejemplo se tuviera más de un objeto, tambien cambiaria las operaciones que las fuerzas hacen sobre el segundo.

Para implementarlo sin problema debe pasarse por valor, para que el valor original de las fuerzas no cambie realmente cada frame.

Una propuesta para lograr esto se encuentra en el texto guia:

``` js
applyForce(force) {
  //{!1} Make a copy of the vector before using it.
  let f = force.copy();
  //{!1} Divide the copy by mass.
  f.div(this.mass);
  this.acceleration.add(f);
}

```
