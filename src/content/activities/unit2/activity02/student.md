
#### ¿Como conseguir la conversión opuesta?


Estoy suponiendo que esto esta preguntando como logre pasar un walker de como estaba en el 0 a vectores y suma de vectores, al seguir leyendo el capitulo 1, explican que efectivamente p5.js no sabe muy bien como sumar vectores cuando solo se ponen a sumar sus nombres, sin embargo mi solución no era la más optima, es usar add()

Por lo que la forma de convertir el codigo es creando vectores con las coordinadas

``` js

let walker;

function setup() {
  createCanvas(640, 240);
  walker = createVector(width/2, height/2);
  background(255);
}

function draw() {
  step();
  show();
}



  function show() 
{
    stroke(0);
    point(walker.x, walker.y);
  }

 function step() 
{
    const choice = floor(random(4));
    if (choice == 0) {
      walker.x++;
    } else if (choice == 1) {
      walker.x--;
    } else if (choice == 2) {
      walker.y++;
    } else {
      walker.y--;
    }
  }

```


Tambien pense que podria crearse vectores para cada dirección, pero considere que seria más trabajo del ideal.

Se ve asi:

![walker](../../../../assets/vectorWalker.png)
