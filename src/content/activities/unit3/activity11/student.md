#### El problema de los n cuerpos

Codigo:

``` js
let bodies = [];
let sun;
function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  for (let i = 0; i < 20; i++) {
    let pos = p5.Vector.random2D();
    let vel = createVector(2,2);
    vel.setMag(random(10, 15));
    pos.setMag(random(100, 150));
    vel.rotate(PI / 2);
    let m = random(10, 15);
    bodies[i] = new Body(pos.x, pos.y, vel.x, vel.y, m);
  }
  sun = new Body(width / 2, height / 2, 0, 0, 400);

}

function draw() {
  background(255, 10);
  sun.pos.x = mouseX;
  sun.pos.y = mouseY;
    sun.show();
  
  //translate(width / 2, height / 2);

  for (let body of bodies) {
    sun.attract(body);
    for (let other of bodies) {
      if (body !== other) {
        body.attract(other);
        stroke(100);
        line(body.pos.x, body.pos.y, other.pos.x, other.pos.y);
      }
    }
  }

  for (let body of bodies) {
    body.update();
    body.show();
  }

}



class Body {
  constructor(x, y, vx, vy, m) {
    this.pos = createVector(x, y);
    this.vel = createVector(vx, vy);
    this.acc = createVector(0, 0);
    this.mass = m;
    this.r = sqrt(this.mass) * 1;
  }

  applyForce(force) {
    let f = p5.Vector.div(force, this.mass);
    this.acc.add(f);
  }

  attract(body) {
    let force = p5.Vector.sub(this.pos, body.pos);
    let distanceSq = constrain(force.magSq(), 100, 1000);
    let G = 1;
    let strength = (G * (this.mass * body.mass)) / distanceSq;
    force.setMag(strength);
    body.applyForce(force);
  }

  update() {
    this.vel.add(this.acc);
    this.pos.add(this.vel);
    this.acc.set(0, 0);
  }

  show() {
    stroke(20);
    strokeWeight(2);
    fill(0, 100);
    ellipse(this.pos.x, this.pos.y, this.r * 2);
  }
}
```

Como se modelo:

Teniendo ya modelada la fuerza de atracción, leyendo el texto guia y siguiendo partes de un codigo dentro de el ya creado para poner más cuerpos interactuando, lo primero que se busca solucionar es que en el ciclo creado para que se apliquen todas las fuerzas entre todos los cuerpos no se termine con un objeto buscando aplicarse sobre si mismo.

Para esto en el codigo se busca primero si el cuerpo a comparar es el mismo o no " if (body ! = other) { body.attract(other);...}

Otras cosas que se cambiaron del codigo anteriormente usado solo para gravedad entre dos objetos fue que se puso un ciclo en el set up para crear 20 objetos con diferentes masas, posiciones y velocidad, y un centro llamado sol que seria el que "los guia" debido a que al tener una masa más grande es el que ejerce mas fuerza de atraccion.

Finalmente hice que la posicion de este sol dependa de donde esta el mouse, para poder moverlo en el canvas y que se evidencie más la interaccion de las fuerzas


[Enlace al codigo en p5.js](https://editor.p5js.org/Mafe-Garcia/sketches/WEz-5z88c)

Resultado:

imagen
