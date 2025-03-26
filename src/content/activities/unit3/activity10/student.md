Modelando fuerzas

Enunciado: diseña varias simulaciones interactivas que muestren cómo modelar fuerzas en tu mundo de pixeles.

Las fuerzas que puedes modelar son las siguientes:

    Fricción.
    Resistencia del aire y de fluidos.
    Atracción gravitacional.

Entrega: el código de cada una de las simulaciones y un texto donde expliques cómo modelaste cada fuerza. Adicionalmente, no olvides incluir un enlace a cada simulación en el editor de p5.js. Para hacer esto recuerda que debes estar logueado en el editor de p5.js y que debes hacer clic en el botón "Save" para guardar los cambios. De esta manera, el enlace a tu simulación se actualizará en la barra de direcciones de tu navegador.


#### Simulacion con modelo de fuerzas:

A continuacion se explicara como se modelaron 3 fuerzas y se aplico en el codigo:

Fricción:


``` js

let mover;

function setup() {
  createCanvas(640, 240);
  mover = new Mover(width / 2, 30, 3);  //aqui se especifica en que luagr del eje x, y aparecera el mover, y la masa de este.
}



function draw() {
  background(255);

  let gravity = createVector(0, 1);
  mover.applyForce(gravity);
  if (mouseIsPressed) {
    let wind = createVector(0.5, 0);
    mover.applyForce(wind);
  }

  if (mover.contactEdge()) {
    let c = 0.1;
    let friction = mover.velocity.copy();  //aqui se adapta la ecuacion de friccion, empezando por multiplicar el vector de velocidad por -1
    friction.mult(-1); // aqui se realizo la multiplicacion emncionada arriba
    friction.setMag(c); // aqui se establece la magnitud, en la ecuacion original esto se da multiplicando el coeficiente de friccion con la fuerza normal, aqui asumimos que la normal es 1, por lo que la magnitud simplemente es el coeficiente de friccion c.
    // Apply the friction force vector to the object.
    mover.applyForce(friction); //aqui se aplica friccion en apply force
  }

  mover.bounceEdges();
  mover.update();
  mover.show();

}







class Mover {
    constructor(x, y, m) {
    this.mass = m;
    this.radius = m * 8;
    this.position = createVector(x, y);
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0, 0);
  }     //parte del constructor se cambio para ser mas similar al del texto guia, de esto tambien dependen algunas partes de la clase mover, anteriormente no tenia radio

  applyForce(force) {
    let f = p5.Vector.div(force, this.mass);  //ya no tiene una masa igual siempre, se puede escoger la masa desde que se crea el mover fuera de la clase
    this.acceleration.add(f);
  }

update() {
  this.velocity.add(this.acceleration);
  this.position.add(this.velocity);
  this.acceleration.mult(0);
}

  show() {
    stroke(0);
    strokeWeight(2);
    fill(127, 127);
    circle(this.position.x, this.position.y, this.radius * 2);
  }

  contactEdge() {
  return (this.position.y > height - this.radius - 1);
}


  bounceEdges() {
  let bounce = -0.9;
  if (this.position.y > height - this.radius) {
    this.position.y = height - this.radius;
    this.velocity.y *= bounce;
  }
}
  
}
```

[Codigo Fricción](https://editor.p5js.org/Mafe-Garcia/sketches/zLqMYo8X5)

¿Como se modelo?

Para esta primera fuerza consulte mucho el texto guia, sin perder de vista los pasos, primero se busca la ecuación de esta fuerza:

imagen

Despues se revisa si hay vectores, que en efecto hay, el de velocidad, como la friccion va en la direccion opuesta a la fuerza normal, se ve en el -1, para el codigo entonces, tenemos que sacar una copia del valor de velocidad, y despues lo multiplicamos por -1

imagen 

Se revisa que más ocurre en la ecuación, falta buscar la magnitud, esta en la ecuación se busca multiplicando mu, el coeficiente de friccion, por la fuerza normal, siguiendo el texto guia, y porque yo tampoco quiero enredarme más, se asume que la normal sera siempre 1 y el coeficiente se deja en 0.1, se podria declarar la normal y el coeficiente y luego multiplicarlos, pero sabiendo que SIEMPRE sera 1, es emjor simplemente poner que la magnitud es igual al coeficiente

imagen

Finalemnte se lleva esta fuerza al applyForce

imagen



Resistencia del Aire y Fluidos:




[Codigo Resistencia del Aire y Fluidos](https://editor.p5js.org/Mafe-Garcia/sketches/-mf0xF3Iq)



¿Como se modelo?

Primero se busca la ecuación de esta fuerza:

imagen

Se revisa el numero en fracción, 1/2 es lo mismo que 0,5, que es más facil de implementar despues

imagen

Despues se revisa si hay vectores, el de velocidad, esta fuerza va en la direccion opuesta a la fuerza normal, se ve en el -, se puede representar con un -1 que se multiplica por todo, para el codigo entonces

imagen 

Se revisa que más ocurre en la ecuación, falta buscar la magnitud, esta en la ecuación se busca multiplicando el coeficiente de resistemcia, por la velocidad al cuadrado, los otros dos valores que se multiplican en la ecuación se ignoran, asumiendo que el objeto es esferico y que la desidad del liquido es 1.

imagen

Finalemnte se lleva esta fuerza al applyForce

imagen




Atracción gravitacional:




[Codigo Atracción Gravitacional](https://editor.p5js.org/Mafe-Garcia/sketches/7yWnHrkG0)



¿Como se modelo?

Primero se busca la ecuación de esta fuerza:

imagen

Se analiza la ecuación, ¿como funciona? Se necesita medir la distacncia entre dos objetos

imagen

Despues se revisa si hay vectores, el de velocidad, esta fuerza va en la direccion opuesta a la fuerza normal, se ve en el -, se puede representar con un -1 que se multiplica por todo, para el codigo entonces

imagen 

Se revisa que más ocurre en la ecuación, falta buscar la magnitud, esta en la ecuación se busca multiplicando el coeficiente de resistemcia, por la velocidad al cuadrado, los otros dos valores que se multiplican en la ecuación se ignoran, asumiendo que el objeto es esferico y que la desidad del liquido es 1.

imagen

Finalemnte se lleva esta fuerza al applyForce

imagen



