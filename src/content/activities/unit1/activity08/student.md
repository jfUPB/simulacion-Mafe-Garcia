#### Creando una aplicación con 3 conceptos: 

Apenas lei las instrucciones de lo que debo hacer se me ocurrio crear una aplicación donde tocando botones se genere un tipo de figura especifica con un tipo de distribución especifica

Tambien [investigue sobre como implementar audio en p5](https://medium.spatialpixel.com/sounds-bd05429aba38), lo encontre muy interesante pero no se si la parte de usar microfono pueda implementala con mi idea inicial



Para la aplicación quiero usar los diferentes tipos de distribución según el boton que se oprima


Referencias visuales:

Por ahora quiero poner la [pagina de Patrik Hubner](https://www.patrik-huebner.com/creative-coding/rgb-shift-loops//)

referencias de cosas que quiero implementar:

[Como agregar botones en P5](https://p5js.org/reference/p5/createButton/)

[Codigo de canvas reconociendo click](https://editor.p5js.org/acedean/sketches/QS3BjapSx)

un codigo que explicac como agregar un boton interactivo:
``` js
let button;

function setup() {
  createCanvas(800, 600);
  button = createButton("BOOP!");
  button.mouseClicked(moveButton);
  button.size(200, 100);
  button.position(10, 10);
  button.style("font-family", "Comic Sans MS");
  button.style("font-size", "48px");
} 

function draw() { 
  background(220);
  /*button.style("font-size",
               map(mouseX, 0, width, 0, 128) + "px");*/
}


function moveButton() {
  button.position(random(width-200), random(height-100));
  console.log("you booped me!");
}
```


Despues de explorar la pagina de Patrik he decidido que lo que quiero es una aplicación donde al oprimir un botón, o al hacer click dentro del canvas (dependera de loq ue crea que se ve mejor al implementarlo) se cambie a un tipo diferente de distribución para formas que apareceran en pantalla, al mismo tiempo su color, tamaño, transpariencia y donde aparecera tendran sus propios tipos de distribución (aun no estoy segura de si ponerlas al azar apenas se haga el click o si cada forma tendra tipos de distribución para estos aspectos ya escogidos).

La función de la aplicación seria solo estetica, lo que no se si sea aceptable pero personalmente me gusta.
