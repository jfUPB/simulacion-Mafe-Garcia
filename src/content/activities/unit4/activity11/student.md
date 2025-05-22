#### Obra generativa algoritmica en tiempo real:

Proceso de construcción:

Quiero hacer algo con los osciladores, me gusta como se ven, quiza pueda hacer algo con sus colores y la cantidad que aparece, siempre me gusta poder mover cosas con el mouse, pero quiza deba experimentar con musica tambien, puede que esos ea lo que cambie los colores

Tengo que buscar como crear diferentes instancias de los osciladores, y que se creen en lugares diferentes, en vez de en el mismo lugar, y que no siempre se sigan sumando


Finalemnte decidi hacer algo muy simple, más que todo porque ahora mismo corro contra reloj y no es solo en una materia, cree un codigo que cada cierto tiempo cambia el color del fondo y agrega más pendulos, estos se pueden agarrar y sobre ellos actua la gravedad


[Este es el editor de la simulación](https://editor.p5js.org/Mafe-Garcia/sketches/BL0qA0Fbo)

Este es el codigo:

``` js
let pendulum;
let pendulum2;
let pendulums=[];

function setup() {
  createCanvas(640, 240);
  background(random(floor(255)), random(floor(255)), random(floor(255)));
  // Make a new Pendulum with an origin position and armlength
  pendulums[0] = new Pendulum(width / 2, 0, 2);
   pendulums[1] =new Pendulum((width / 2)+10, 0, 4);  
}



function draw() {
  console.log(frameCount);
 if(frameCount%120==0)
   {
     background(random(floor(255)), random(floor(255)), random(floor(255)));
     for (let i = 0; i < pendulums.length; i++) {
    pendulums[i].r=pendulums[i].r+2;
  }
     
   }
  
  
   if(frameCount%2400==0)
   {
     pendulums.push(new Pendulum((width / 2), 0, random(floor(20))));
  }
     
   
  for (let i = 0; i < pendulums.length; i++) {
    pendulums[i].update();
    pendulums[i].show();
    pendulums[i].drag(); 
  }
  
   // for user interaction
  
    
}

function mousePressed() {
  for (let i = 0; i < pendulums.length; i++) {
    pendulums[i].clicked(mouseX, mouseY);
  }
}

function mouseReleased() {
  for (let i = 0; i < pendulums.length; i++) {
    pendulums[i].stopDragging();
  }
}

```

Captura:
