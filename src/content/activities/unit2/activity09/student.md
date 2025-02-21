Experimentando con la aceleración

Enunciado: en el libro proponen una regla (que eventualmente se rompe cuando conviene :)):

The goal for programming motion is to come up with an algorithm for calculating acceleration and then let the trickle-down effect work its magic.

Para investigador el significado de esta frase te propone que construyas un experimento donde analices cómo se comporta un objeto en movimiento con:

    Aceleración constante.
    Aceleración aleatoria.
    Aceleración hacia el mouse.

Entrega:

    Reporta que encontraste para cada una de las posibles aceleraciones
    ¿Por qué?

#### Aceleracion


La aceleración describe como cambia la velocidad a lo largo del tiempo, dentro del texto guia se habla de tres tipos de aceleración:


1. Aceleración constante: Como lo dice su nombre, la velocidad va subiendo de forma constante, usualmente se le pone un limite para que deje de subir apenas llegue a este; esta se declara desde la clase del mover.
2. Aceleración aleatoria: Esta aceleración es aleatoria, como lo explica su nombre, no se usa solo para afectar la velocidad, si no la magnitud y la dirección de la proxima posición
3. Esta aceleración depende de la posicion del mouse, se crea un vector con la posicion original y la pisicion actual del mouse,  y se le asigna una aceleracion para que vaya acercandose al mouse.



En el texto guia se vio ejemplos de todos:

Aceleración constante:

``` js

  update() {

    this.velocity.add(this.acceleration);
    this.velocity.limit(this.topSpeed);

Velocity changes by acceleration and is limited by topSpeed.

    this.position.add(this.velocity);

  }


```

Aceleración aleatoria:

``` js

let mover;

function setup() {
  createCanvas(700, 700);
  // Create the Mover object.
  mover = new Mover();
}

function draw() {
  background(255);
  // Call methods on the Mover object.
  mover.update();
  mover.checkEdges();
  mover.show();
}
class Mover {

  constructor() {

    this.position = createVector(width / 2, height / 2);

    this.velocity = createVector(0, 0);

    this.acceleration = createVector(-0.001, 0.01);


    this.topSpeed = 10;



  }

update() {

  this.acceleration = p5.Vector.random2D();
  this.velocity.add(this.acceleration);
  this.velocity.limit(this.topSpeed);
  this.position.add(this.velocity);


}



  show() {
    stroke(0);
    strokeWeight(2);
    fill(127);
    circle(this.position.x, this.position.y, 48);
  }

  checkEdges() {
    if (this.position.x > width) {
      this.position.x = 0;
    } else if (this.position.x < 0) {
      this.position.x = width;
    }

    if (this.position.y > height) {
      this.position.y = 0;
    } else if (this.position.y < 0) {
      this.position.y = height;
    }
  }
}

```

Aceleración al mouse:

``` js

// Declare the Mover object.
let mover;

function setup() {
  createCanvas(700, 700);
  // Create the Mover object.
  mover = new Mover();
}

function draw() {
  background(255);
  // Call methods on the Mover object.
  mover.update();
  mover.checkEdges();
  mover.show();
}
class Mover {

  constructor() {

    this.position = createVector(width / 2, height / 2);

    this.velocity = createVector(0, 0);

    this.acceleration = createVector(-0.001, 0.01);


    this.topSpeed = 10;



  }

  update() {
    let mouse = createVector(mouseX, mouseY);
    // Step 1: Compute the direction.
    let dir = p5.Vector.sub(mouse, this.position);
    // Step 2: Normalize.
    dir.normalize();
    // Step 3: Scale.
    dir.mult(0.2);
    //{!1} Step 4: Accelerate.
    this.acceleration = dir;
    this.velocity.add(this.acceleration);
    this.velocity.limit(this.topSpeed);
    this.position.add(this.velocity);
  }


  show() {
    stroke(0);
    strokeWeight(2);
    fill(127);
    circle(this.position.x, this.position.y, 48);
  }

  checkEdges() {
    if (this.position.x > width) {
      this.position.x = 0;
    } else if (this.position.x < 0) {
      this.position.x = width;
    }

    if (this.position.y > height) {
      this.position.y = 0;
    } else if (this.position.y < 0) {
      this.position.y = height;
    }
  }
}

```
