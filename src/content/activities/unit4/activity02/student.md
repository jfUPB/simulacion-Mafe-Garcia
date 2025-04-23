#### Sobre estas simulaciones:

Sobre [la simulación sobre angulos](https://editor.p5js.org/juanferfranco/sketches/R1iTVQjzm)

1. ¿Que esta pasando en esta simulación?   Se puede poner a "rotar" una linea con dos circulos, puede ser con teclas o de forma automatica cuando empieza a correr el codigo, realmente estan rotando todas las coordenadas de x & y, y despues de rotar se imprimen los objetos, lo que da la ilusión de que el objeto se mueve.
2. ¿Cual es la interacción? El presionar cualquier tecla del teclado, es lo que hace que el objeto rote.
3. ¿Por que crees que en cada frame se esta trasladando el origen del sistema de coordenadas al centro de la pantalla?  Por el translate(), este cambia el origen de las coordinadas a donde se decida, que en el codigo fue la mitad de height y width, es decir, el centro del canvas
4. ¿Cual es la relación entre el sistema de coordenadas y la función rotate()? Esta función tiee el poder de rotar todo el sistema de coordenadas segun lo que se escriba en el parentesis, en este caso, es segun la variable angle, que puede subir segun se presione teclas, o automaticamente.
5. Parece que loe elemntos graficos siempre se estan dibujando en la posicion (0,0), ¿Por que crees que se hace esto?  Por que se rota a partir de este centro, es necesario que partan de ahi para que parezca que son ellos los que rotan.
6. ¿Por qué aunque en cada frame se hace lo mismo, los elementos gráficos rotan? Porque se esta rotando todo el sistema de coordenadas, por lo que ahora el -50 se encuentra más arriba que antes, y asi con las demas coordenadas


Sobre [la simulación donde se puede escoger a donde apuntan objetos](https://editor.p5js.org/natureofcode/sketches/bZqHGYbRQ)

1. Identifica el motion 101, ¿Que esta haciendo en este marco?   Se ve en esta imagen: IMAGEN De forma muy resumida, esta estableciendo que originalemnte tiene una velocidad y aceleración de 0, que cambia segun donde este el mouse, con un vector que contiene las coordenadas del mouse, el mover buscar llegar a este sin parar, en la parte de display imprime en cada frame donde iria el objeto "buscando" el mouse.
2. ¿Que hace la función heading()?  Esta se me ha dificultado entenderla más que otras que apenas descubro en esta actividad, por lo que entiendo, registra el angulo que crea un vector respecto al origen de las coordenadas, pero no he entendido muy bien como funciona, o como ayuda en este codigo en especifico.
3. ¿Que hace la función push() y pop()? Funcionan como duo, y sirven para crear "grupos" de dibujo, asi cada parte de uno o varios dibujos funciona de forma independiente al resto del sketch en el codigo, experimente con [un ejemplo que se encuentra en la documentacion de p5](https://p5js.org/reference/p5/push/), quitando push y pop en varias partes del codigo, para algunos se enloquecia el lugar donde aparecian las cosas, para otros hacia que se movieran más objetos de los que queria
4. ¿Que hace rectMode(CENTER)? Este metodo hace que la proxima forma a crear empiece desde su centro, toma los primeros 2 valores como el origen de la forma a hacer, y los siguientes valores como su altura y ancho.
5. ¿Cual es la relación entre el angulo de rotacion y el vector de velocidad?  El angulo de rotación le importa a la velocidad porque es usando este por mediod e heading que se determina la velocidad con la que voltea a buscar el mouse.
6. Trata de dibujar en un papel el vector de velocidad y como se relaciona con el angulo de rotación y la operación de traslacion y rotación
