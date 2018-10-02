El HTML del juegoSection
La estructura del documento HTML es muy simple, porque todo el juego se visualizará dentro del elemento <canvas>. Con tu editor de textos favorito, prepara un documento en blanco, guárdalo como index.html en un lugar adecuado, y escribe el siguiente código:
	...
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <title>Gamedev Canvas Workshop</title>
    <style>
    	* { padding: 0; margin: 0; }
    	canvas { background: #eee; display: block; margin: 0 auto; }
    </style>
</head>
<body>

<canvas id="myCanvas" width="480" height="320"></canvas>

<script>
	// JavaScript code goes here
</script>

</body>
</html>
      ...
En la cabecera (head) tenemos un charset, el título de la página <title> y un poco de CSS básico. El <body> contiene los elementos<canvas> y <script>. Representaremos el juego en el primero y escribiremos el código JavaScript que lo controla en el segundo. El elemento  <canvas> tiene el id myCanvas para que podamos hacer referencia a él con facilidad, y mide 480 píxeles de ancho por 320 de alto. Todo el código JavaScript que vamos a escribir en este tutorial lo pondremos entre las etiquetas <script> y </script>.

El lienzo (canvas)Section
Para que podamos visualizar los gráficos en el elemento <canvas>, primero tenemos que preparar una referencia a él en JavaScript. Añade lo siguiente después de la etiqueta <script>:
	...
var canvas = document.getElementById("myCanvas");
var ctx = canvas.getContext("2d");
	...
Aquí estamos guardando una referencia al elemento <canvas> en la variable canvas. Después estamos creando la variable ctx para guardar el contexto de gráficos 2D, que es la herramienta  que realmente utilizaremos para dibujar.

Veamos un fragmento de código de ejemplo que dibuja un cuadrado rojo en el canvas. Añade el código a continuación y abre el archivo index.html con un navegador para comprobar que funciona:
        ...
ctx.beginPath();
ctx.rect(20, 40, 50, 50);
ctx.fillStyle = "#FF0000";
ctx.fill();
ctx.closePath();
        ...
Todas las instrucciones están entre los métodos beginPath() y closePath(). Estamos definiendo un rectángulo utilizando rect(): los dos primeros valores especifican las coordenadas de la esquina superior izquierda del rectángulo en el canvas, y  los otros dos sirven para indicar el ancho y el alto. En nuestro caso, el rectángulo se dibuja a 20 píxeles desde la izquierda de la pantalla y 40 píxeles desde la parte de arriba, y tiene 50 píxeles de ancho y 50 de alto, con lo que obtenemos un cuadrado perfecto. La propiedad fillStyle guarda un color que utilizará el método fill() para pintar el cuadrado que, en nuestro caso, será rojo.

Podemos dibujar otras cosas aparte de rectángulos. Aquí hay un fragmento de código que dibuja un círculo verde. Prueba a añadir esto al final de tu código JavaScript, guárdalo y recarga la página en el navegador:
       ...
ctx.beginPath();
ctx.arc(240, 160, 20, 0, Math.PI*2, false);
ctx.fillStyle = "green";
ctx.fill();
ctx.closePath();
       .    ..
 Como puedes ver, estamos utilizando otra vez los métodos beginPath() y closePath(). De lo que hay en medio, la parte más importante del código anterior es el método arc(). Tiene seis parámetros:

las coordenadas x e y del centro del arco
el radio del arco
los ángulos inicial y final (en qué ángulo empezar y terminar de dibujar el círculo, en radianes)
la dirección hacia la que se dibujará (false para seguir el sentido de las agujas del reloj, que es el valor por defecto, o true para el sentido contrario). Este parámetro es opcional.
La propiedad fillStyle tiene un valor distinto al que habíamos puesto antes. Esto se debe a que, como ocurre en CSS, el color se puede especificar como un valor hexadecimal, como un nombre de color en inglés, la función rgba(), o cualquiera de los otros métodos de descripción de color que existen.

En lugar de utilizar fill() y rellenar las formas con colores, podemos utilizar stroke() para colorear únicamente el trazo exterior. Prueba a añadir también esto a tu código JavaScript:
       ...
ctx.beginPath();
ctx.rect(160, 10, 100, 40);
ctx.strokeStyle = "rgba(0, 0, 255, 0.5)";
ctx.stroke();
ctx.closePath();
       ...
El código anterior dibuja un rectángulo vacío con el perímetro azul. Gracias al canal alfa de la función rgba(), que es el cuarto valor (Red, Green, Blue, Alpha), el color azul será medio transparente.
       ...
Compara tu códigoSection
Aquí está el código fuente completo de la primera lección, ejecutándose en un JSFiddle:
       ...
var canvas = document.getElementById("myCanvas");
var ctx = canvas.getContext("2d");

ctx.beginPath();
ctx.rect(20, 40, 50, 50);
ctx.fillStyle = "#FF0000";
ctx.fill();
ctx.closePath();

ctx.beginPath();
ctx.arc(240, 160, 20, 0, Math.PI*2, false);
ctx.fillStyle = "green";
ctx.fill();
ctx.closePath();

ctx.beginPath();
ctx.rect(160, 10, 100, 40);
ctx.strokeStyle = "rgba(0, 0, 255, 0.5)";
ctx.stroke();
ctx.closePath();
       ...
