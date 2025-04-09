#### Metodo lerp()


Por lo que veo experimentando cambiar el valor de lerp() en el codigo proveido es como que escoge el angulo al que saldra el tercer vector, tomando los posibles angulos entre 2 de estos como si fueran de 0 a 1.

lerpColor() funciona igual pero con un gradiante entre dos colores.

Se dibuja una flecha con drawArrow() poniendo primero el vector del que se origina la flecha, luego el vector que se le suma para crear la flecha y finalmente el color que tendra la flecha.

Este fue el codigo que diseñe, las flechas no son del mismo largo que la imagen pero  hace esencialmente lo mismo:

``` js
let x = 0;
isit = true;
function setup() {
    createCanvas(200, 200);
}

function draw() {
    background(200);

    let v0 = createVector(100, 100);
    let v1 = createVector(60, 0);
    let v2 = createVector(0, 60);
    let v4 = createVector(160, 100);
  let v5= createVector(-60, 60)
  if(isit==true)
    {
      x+=0.01;
      if(x>=1)
        {
          isit= false;
        }
    }
  else
    {
       x-=0.01;
      if(x<=0)
        {
          isit= true;
        }
    }
    console.log(x);
  
    let v3 = p5.Vector.lerp(v1, v2, x);      
    drawArrow(v0, v1, 'red');
    drawArrow(v0, v2, 'blue');
    drawArrow(v0, v3, lerpColor('red','blue', x));
    drawArrow(v4, v5, 'green')
    
}

function drawArrow(base, vec, myColor) {
    push();
    stroke(myColor);
    strokeWeight(3);
    fill(myColor);
    translate(base.x, base.y);
    line(0, 0, vec.x, vec.y);
    rotate(vec.heading());
    let arrowSize = 7;
    translate(vec.mag() - arrowSize, 0);
    triangle(0, arrowSize / 2, 0, -arrowSize / 2, arrowSize, 0);
    pop();
}
```
