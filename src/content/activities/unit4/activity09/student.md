#### Resortes:

[Enlace a la simulación](https://editor.p5js.org/Mafe-Garcia/sketches/htgvvHZnM)


Codigo de la simulación:

``` js
let bob;

// Spring object
let spring;

function setup() {
  createCanvas(640, 240);
  // Create objects at starting position
  // Note third argument in Spring constructor is "rest length"
  spring = new Spring(width / 2, 10, 100);
  bob = new Bob(width / 2, 100);
  bob2= new Bob(bob.position.x, bob.position.y, 10, 50);
  spring2= new Spring(bob.position.x, bob.position.y, 10, 600);
}

function draw() {
  background(255);

  // Apply a gravity force to the bob
  let gravity = createVector(0, 2);
  bob.applyForce(gravity);
  bob2.applyForce(gravity);


  // Update bob
  bob.update();
  bob.handleDrag(mouseX, mouseY);
  
  bob2.update();
  bob2.handleDrag(mouseX, mouseY);

  // Connect the bob to the spring (this calculates the force)
  spring.connect(bob);
  
  spring2.connect(bob2);

  // Constrain spring distance between min and max
  spring.constrainLength(bob, 30, 200);
  
  spring2.constrainLength(bob2, 30, 200);

  // Draw everything
  spring.showLine(bob); // Draw a line between spring and bob
  bob.show();
  spring.show();
  
  spring2.showLine(bob2); // Draw a line between spring and bob
  bob2.show();
  spring2.show();
}

function mousePressed() {
  bob.handleClick(mouseX, mouseY);
  bob2.handleClick(mouseX, mouseY);
}

function mouseReleased() {
  bob.stopDragging();
  bob2.stopDragging();
}

class Spring {
  constructor(x, y, length) {
    this.anchor = createVector(x, y);
    this.restLength = length;
    this.k = 0.2;
  }
  // Calculate and apply spring force
  connect(bob) {
    // Vector pointing from anchor to bob location
    let force = p5.Vector.sub(bob.position, this.anchor);
    // What is distance
    let currentLength = force.mag();
    // Stretch is difference between current distance and rest length
    let stretch = currentLength - this.restLength;

    //{!2 .bold} Direction and magnitude together!
    force.setMag(-1 * this.k * stretch);

    //{!1} Call applyForce() right here!
    bob.applyForce(force);
  }

  constrainLength(bob, minlen, maxlen) {
    //{!1} Vector pointing from Bob to Anchor
    let direction = p5.Vector.sub(bob.position, this.anchor);
    let length = direction.mag();

    //{!1} Is it too short?
    if (length < minlen) {
      direction.setMag(minlen);
      //{!1} Keep position within constraint.
      bob.position = p5.Vector.add(this.anchor, direction);
      bob.velocity.mult(0);
      //{!1} Is it too long?
    } else if (length > maxlen) {
      direction.setMag(maxlen);
      //{!1} Keep position within constraint.
      bob.position = p5.Vector.add(this.anchor, direction);
      bob.velocity.mult(0);
    }
  }

  //{!5} Draw the anchor.
  show() {
    fill(127);
    circle(this.anchor.x, this.anchor.y, 10);
  }

  //{!4} Draw the spring connection between Bob position and anchor.
  showLine(bob) {
    stroke(0);
    line(bob.position.x, bob.position.y, this.anchor.x, this.anchor.y);
  }
}


```


![resorte](../../../../assets/resortes.png)
