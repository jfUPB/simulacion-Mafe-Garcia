
#### Sobre la clase p5.Vector:

El metodo mag() sirve para calcular la magnitud del vector, mientras que magSq() sirve para calcular la magnitud del vector al cuadrado, no sabria decir si uno es más eficiente, por ahora creo que tienen funciones diferentes aunque se vean similares, sirve más la que se acomod emejor a la necesidad de la aplicación. 

Al periodista me gustaria decirle como dijo en su momento un idolo mio: primero que todo, ¿Quien es usted?, segundo que todo, yo no soy su amigo, y tercero, que le importa.


Pero realmente le diria: ah pues es un metodo que te da el producto punto entre dos vectores. La verdad no entendi muy bien la diferencia entre la implementación y uso de la version estatica y de instancia, investigando los conceptos por si solos [aqui](https://dotnetustad.com/c-sharp/static-vs-Instance-methods), entendi que cuando se trata de version de instancia no hay necesidad de crear una clase, en este contexto asumo que se referiria a crear el vector, mientras que para la estatica si debe hacerlo.

Con el paralelogramo se puede hacer una intuición geometrica del prodcuto cruz, mas especificamente con el area de este:


![walker](../../../../assets/intuicioncruz.png)

Para encontrar su area debe multiplicarse su base por la longitud de su lado, estas dos medidas pueden verse como vectores, cuando se multiplica se da el producto cruz, el vector resultante de esto debe ser el que mira hacia arriba t es perpendicular a uno de los vectores anteriores


El metodo dist() funciona para calcular una distancia dentro de dos o tres dimensiones, tambien existe p5.Vector.dist() para cuando se use para calcular distancia entre dos versiones.

El metodo normalize escala los componentes de un vector para que su magnitud sea 1.

Limit pone un limite maximo a la magnitud de un objeto.
