#### Coordenadas polares:

¿Que relacion existe entre r y theta y x y y?

Viendo lo que son las coordenadas polares, que en vez de basarse en una posicion en el eje x y en el eje y, se arma con la distancia y el valor de un angulo; Para pasar de coordenadas polares a cartesianas, se usa el SohCahToa, usando el angulo que se sabe cual es (theta) y la distancia de la hipotenusa (r) se puede buscar la distancia se los otros lados que formaria el triangulo hecho con la distancia y el angulo, los lados corresponden a los puntos x y y de las coordenadas cartesianas, más información puede encontrarse [aqui](https://www.disfrutalasmatematicas.com/graficos/coordenadas-polares-cartesianas.html) y [aqui](https://www.studypug.com/es-trigonometry-help/utilizando-soh-cah-toa)

¿Que ocurre si se modifica la función draw del ejemplo por esto?

``` js
 function draw() {
  background(255);
  // Translate the origin point to the center of the screen
  translate(width / 2, height / 2);
  let v = p5.Vector.fromAngle(theta);
  fill(127);
  stroke(0);
  strokeWeight(2);
  line(0, 0, x, y);
  circle(v.x, v.y, 48);
  theta += 0.02;
}
```

Aparece un error en consola que dice "x is not defined"

¿Por qué?

Porque nunca se define x en ninguna parte como en el codigo inicial, usando fromAngle tampoco tiene magnitud, solo angulo.


¿Que ocurre si se modifica la función draw del ejemplo por esto otro?

``` js
 function draw() {
  background(255);
  // Translate the origin point to the center of the screen
  translate(width / 2, height / 2);
  let v = p5.Vector.fromAngle(theta,r);
  fill(127);
  stroke(0);
  strokeWeight(2);
  line(0, 0, v.x, v.y);
  circle(v.x, v.y, 48);
  theta += 0.02;
}
```

Ahora funciona bien como al inicio pero el codigo es más corto y ordenado

¿Por qué?

Ahora se guardan theta y r en un solo vector, y con fromAngle se crea un vector 2d usando el angulo de theta y la distancia de r, y de ahi salen las nuevas x y y

