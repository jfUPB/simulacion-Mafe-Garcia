#### Ola:
Lo intente, y medio dio, pero quedo rara:

[Enlace a la simulación](https://editor.p5js.org/Mafe-Garcia/sketches/Whg_-SAWa)

Codigo de la simulación:

``` js

let angle = 0;
let angleVelocity = 0.2;
let amplitude = 100;
let what = true;
let v=0;

function setup() {
  createCanvas(640, 240);
  background(255);

  stroke(0);
  strokeWeight(2);
  fill(127, 127);

  for (let x = 0; x <= width; x += 24) {
    // 1) Calculate the y position according to amplitude and sine of the angle.
    let y = amplitude * sin(angle);
    // 2) Draw a circle at the (x,y) position.
    if (y>90)
      {
        what=false;
      }
    else if (y<-99)
      {
        what=true;
      }
    else
      {
        what=what;
      }
    
    if(what==true)
      {
        fill('blue');
        circle(v, y + height / 2, 48);
    // 3) Increment the angle according to angular velocity.
    angle += angleVelocity;
        console.log(v);
      }
    else if(what==false)
      {
        fill('pink');
        circle(x, y + height / 2, 48);
    // 3) Increment the angle according to angular velocity.
    angle += angleVelocity;
        v=x;
      }
    
  }
}


```

Captura:

