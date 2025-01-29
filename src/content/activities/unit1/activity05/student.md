Distribución Normal

Enunciado: implementa un ejemplo que genere números aleatorios con una distribución normal (gaussiana). Visualiza la distribución utilizando figuras geométricas.

Entrega:

    Código del ejemplo
    Captura de pantalla
    Una breve explicación de cómo se refleja la distribución normal en la visualización.


#### Visualización de la distribución Gaussiana con figuras geometricas

Intentare crear un codigo que muestre una diferente figura dependiendo del número que salga de un randomGaussian()

Mi experimento inicial sera con media 5 y desviación estandar 3, si el número es 4, 5 o 6, se creara un triangulo naranja, si es un número menor a 4 sera un cuadrado azul y si es mayor que 4 sera un circulo rosa

Este fue mi primer intento:

imagen 1


Si bien tecnicamente funciona, no se puede distinguir mucho los resultados ni que tan frecuentes son, por lo que intentare poner un contador para que sea cada 20 segundos, tambien agregare los colores:


