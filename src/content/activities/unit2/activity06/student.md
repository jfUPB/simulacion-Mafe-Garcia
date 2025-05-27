
#### Cambiando origen y escala con el mouse

Este es el codigo que cree para poder modificar la base de las flechas, asumiendo que se refiere al origen de estas, y la escala o longitud de los vectores

Para este codigo ambas cosas se cambian cada que se hace click

``` js
let o = 100;
let h = 60;
let x = 0;
isit = true;
function setup() {
createCanvas(200, 200);
}

function mousePressed() { 
  o = floor(random(201));
  h = floor(random(100));
}

function draw() {
    background(200);
    
    

    let v0 = createVector(h, h);
    let v1 = createVector(o, 0);
    let v2 = createVector(0, o);
    let v4 = createVector(v0.x+o, v0.y);  // Aqui estoy haciendo que la flecha verde siempre quede bien dependiendo de v0
  let v5= createVector(-o, o)
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


Inicialmente busque cuales eran las relaciones entre todos los vectores, como depende uno de los valores del otro, conclui que se necesitaba una variable para el punto de origen de 3 de las flechas y otro para la longitud de las flechas, los llame h y o respectivamente

Despues intente usar el mouseClicked igual que en una actividad en la unidad pasada, pero como habia tenido problemas en su momento con que siguiera un loop en un codigo que usa esto, busque como más podia implementarlo y encontre la función mousePressed, esta deja que el loop siga, asi se puede ver ocmo se mueven las flechas en su ultimo lugar, y cuando se presiona el click se realiza algo, en mi caso ponia un random para las dos variables que luego serian usadas para cambiar el origen y la longitud de las flechas

Tambien vi funciones que detectan porque lado del canvas se encuentra el mouse pero no las use
