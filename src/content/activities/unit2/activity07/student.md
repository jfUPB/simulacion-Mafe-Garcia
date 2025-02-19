Motion 101

Entrega: ahora vas a leer y analizar con mucho detenimiento la sección Motion with vectors. El autor propone un marco de movimiento llamado motion 101.

¿En qué consiste motion 101?

Entrega: la respuesta a la pregunta e ilustra con un ejemplo.

#### Motion 101 

El Motion 101 en los terminos más sencillos, se refiere a primero tomar un vector que determina una posicion 1, agregarle velocidad, es decir, sumar a los valores del vector existente, ahora representa otra posicion 2, despues dibujar un objeto determinado en esta posición, y seguir asi 

Este es el ejemplo encontrado en el texto guia:

``` js

let mover;

function setup() {
  createCanvas(640, 240);
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

La forma en la que funciona es primero creando un mover, es una clase que crea una posicion inicial random y una velocidad, despues el mover pasa por update, donde se le agrega la velocidad al vector de posicion, despues va a check edges, donde revisa si se ha pasado de los bordes del canvas, si si entonces los lleva al otro extremo de este, finalmente mover pasa por show, que crea la bolita que aparecera en la posicion, esto se repite cada frame, y crea la ilusion de que se mueve dentro del canva
