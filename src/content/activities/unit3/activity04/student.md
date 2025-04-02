Marco Motion 101

Entrega: ¿Recuerdas el marco motion 101 de la unidad anterior? Regresa y dale una mirada rápida si es del caso. Luego considera lo siguiente:

let mover;

function setup() {
    createCanvas(640, 240);
    mover = new Mover();
}

function draw() {
    background(255);
    mover.show();
    mover.update();
    mover.checkEdges();
}

.
.
.


update() {

    // Aquí calculo la aceleración
    .
    .
    .
    this.velocity.add(this.acceleration);
    this.velocity.limit(this.topSpeed);
    this.position.add(this.velocity);
}
.
.
.

Mira bien el código. ¿Dónde está el marco motion 101?

    En la unidad anterior tu definías la aceleración mediante algún algoritmo. ¿Cuáles eran? Muestra ejemplos de código de la unidad anterior (solo la parte donde se define la aceleración).
    En esta unidad tu vas a calcular la aceleración. ¿Qué tiene que ver esto con las leyes de movimiento de Newton?

Entrega: texto y fragmentos de código donde des respuesta a cada una de las preguntas anteriores.


#### ¿Donde esta el motion 101?

En la unidad anterior se definia la aceleración por medio de algoritmos como este:

``` js

  update() {

    this.velocity.add(this.acceleration);
    this.velocity.limit(this.topSpeed);

Velocity changes by acceleration and is limited by topSpeed.

    this.position.add(this.velocity);

  }

```


``` js

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
```

``` js
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

```

El que yo calcule la aceleracion tiene que ver con las leyes de Newton porque esta depende e las fuerzas que se ejerzan sobre x objetos
