#### ¿Qué pasaria si...?


Viendo el codigo del ejemplo, pienso, que pasaria si agregara un elemento aleatorio a la velocidad? controlada por clicks, tambien me pregunto si podre de alguna forma ahi mismo hacer que la velocidad sea negativa, que creo, en teoria, debe hacer que la bolita vaya al otro lado.



Esta fue mi propuesta original:

``` js

// Declare the Mover object.
let mover;

function setup() {
  createCanvas(640, 240);
  // Create the Mover object.
  mover = new Mover();
}

function mousePressed() { 
  mover.velocity.x = (random(-20, 20));
  mover.velocity.y = (random(-20, 20));
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
    // The object has two vectors: position and velocity.
    this.position = createVector(random(width), random(height));
    this.velocity = createVector(random(-2, 2), random(-2, 2));
  }

  update() {
    // Motion 101: position changes by velocity.
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

Cada vez que hacia click si cambiaba la velocidad y la dirección a la que se dirigia la pelota, el problema es que la velocidad solo pasaba entre los dos numeros en el random, esto porque al hacer el (-20, 20) no se refiere a un intervalo entre ambos, si no que ambos son los unicos posibles resultados del random

Lo que quiero es que la velocidad cambie dentro de ese intervalo, por lo que busque como implementar intervalos en java dentro de un random usando negativos y positivos.

[Esto fue lo que mas me ayudo](https://stackoverflow.com/questions/13455042/random-number-between-negative-and-positive-value), ahi se ve diferente el codigo pero creo que lo puedo adaptar para el mio:


Esta fue mi version mejorada:

``` js

// Declare the Mover object.
let mover;

function setup() {
  createCanvas(640, 240);
  // Create the Mover object.
  mover = new Mover();
}

function mousePressed() { 
  mover.velocity.x = (random(20));
  mover.velocity.x *= round(random(-1, 1));
  mover.velocity.y = (random(20));
  mover.velocity.y *= round(random(-1, 1));
  console.log(mover.velocity.x, " y ", mover.velocity.y);
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
    // The object has two vectors: position and velocity.
    this.position = createVector(random(width), random(height));
    this.velocity = createVector(random(-2, 2), random(-2, 2));
  }

  update() {
    // Motion 101: position changes by velocity.
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

Esta version logro lo que queria, con el console.log tambien puedo verificarlo
