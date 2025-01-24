Vas a realizar un experimento con el código:

Comprende el código, entiende lo que pasa y cómo se está aplicando el concepto.
Luego harás una modificación al código. Te harás esta pregunta ¿Qué pasaría si?
Trata de lanzar una hipótesis de lo que crees que ocurrirá.
Realiza la modificación.
Vas a documentar

Describe el experimento que vas a realizar.
¿Qué pregunta quieres responder con este experimento?
¿Qué resultados esperas obtener?
¿Qué resultados obtuviste?
¿Qué aprendiste de este experimento?
Entrega: los asuntos que te pido documentar en el enunciado, el código con las modificaciones y una captura de pantalla que muestre el resultado del experimento.

##### Comprensión del codigo:

``` js


let walker;                                // por convencion de p5.js seu sa let para declarar cualquier variable

function setup() {                        //pone todo lo inicial (tamaño del canvas, color y la funcion walker
  createCanvas(640, 240);
  walker = new Walker();
  background(255);
}

function draw() {                        // funcion draw, lleva a los metodos show y step, que son los que pintan y escogen la siguiente dirección para pintar 
  walker.step();
  walker.show();
}
   
class Walker {                           // detalles del walker, inicia en la mitad de la pantalla, sus coordinadas vistas en los objetos x y y, que son la mitad del ancho y el alto
  constructor() {
    this.x = width / 2;
    this.y = height / 2;
  }

  show() {                                //show pinta el punto negro, con stroke en las coordinadas x y y
    stroke(0);
    point(this.x, this.y);
  }

  step() {                               // step decide por medio de un random la proxima posicion del walker, cambiando los valores de x y y dependiendo del eandom    
    const choice = floor(random(4));      
    if (choice == 0) {
      this.x++;
    } else if (choice == 1) {
      this.x--;
    } else if (choice == 2) {
      this.y++;
    } else {
      this.y--;
    }
  }
}
```

##### ¿Qué pasaria si...?

¿Qué pasaria si intento cambiar el color o la intensidad del trazo?

Inicialmente hice pequeños experimentos viendo si era posible cambiar el color del stroke, solo cambiando esto:

``` js

  stroke(90);     // ---> fui cambiando por diferentes numeros el numero en el parentesis, sospechando que era el color del trazo igual que el 255 del canvas es el blanco de fondo

```
Pensaba que entre los numeros podria encontrar algun color, pero parece ir en una escala de negro a blanco con grises.


Investigue un poco (y un poco es un poco) stroke en javascript y vi que en uno de los sitios explicando su uso habia un ejemplo con más colores:

## aqui va imagen

me enredaba un poco el uso de ctx y la forma en la que se declaro el canvas, pero intente implementarlo, siempre que le daba play surgia un error, intente usar el getcontext pero creo que eso cambio como funciona todo el codigo porque entonces no podia acceder a walker sin poner esa clase primero y tenia más problemas parecidos a este.

Finalmente hice que fuera cambiando según se iba moviendo, creando un metodo donde cada paso se genere un numero al azar entre 0 y 255 (con floor para que se redondee) y asi determina el tono que tendra el trazo cada paso, tambien cambie el fondo por un gris (230)

Sospecho que se podria hacer algo mas interesante con el uso de un contador que pueda crear limites de tiempo en los que use cierto color o solo vaya a una dirección pero creo que he pasado mucho más tiempo del que deberia en esta pregunta entonces quiero mostrar los pequeños cambios que hice hasta ahora:

``` js

  let walker;


function setup() {
  createCanvas(640, 240);
  walker = new Walker();
  background(230);
}

function draw() {
  walker.intensity();
  walker.step();
  walker.show();
}

class Walker {
  constructor() {
    this.x = width / 2;
    this.y = height / 2;
    this.k = 0;
  }

  show() {
    stroke(this.k);
    point(this.x, this.y);
  }

  step() {
    const choice = floor(random(4));
    if (choice == 0) {
      this.x++;
    } else if (choice == 1) {
      this.x--;
    } else if (choice == 2) {
      this.y++;
    } else {
      this.y--;
    }
  }
  intensity(){
  const intense = floor(random(255));
  this.k = intense;
  }

}

```

Este fue el resultado hasta el que llego en el momento en el que realice la actividad:
