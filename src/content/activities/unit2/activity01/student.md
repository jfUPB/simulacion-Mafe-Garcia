Analiza una aplicación interactiva

Enunciado: analiza el ejemple: Example 1.2: Bouncing Ball with Vectors!

    ¿Cómo funciona la suma dos vectores?
    ¿Por qué esta línea position = position + velocity; no funciona?

Entrega: escribe en tu bitácora la solución a las preguntas anteriores.

#### Suma de vectores:

La forma en la que se suman los vectores, al menos visualmente, es poniendo el final de uno en el inicio del otro, y creando una raya entre los dos puntos más distantes, asi se ve el vector resultante.

de forma (a, b) + (c, d) = (a+c, b+d)

donde (a, b) es un vector , (c, d) es el vector que se le suma y el resultado es un tercer vector

¿ por que no funcionala la siguiente linea?

``` js
position = position + velocity
```

La razón por la que no creo que funcione es que no especifica que parte del vector se suma a que parte del vector.

Pensaria entonces que debe hacerse por cada uno:

``` js
position.x = position.x + velocity.x
position.y = position.y + velocity.y
```
