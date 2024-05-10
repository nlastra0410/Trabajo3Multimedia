paginaweb by HTML5 UP


Instrucciones:

Descripción general
========

Los navegadores manejan las páginas de desplazamiento lateral de manera diferente a las orientadas verticalmente.
que requieren elementos (o al menos, el elemento contenedor superior) para
tener un ancho definido (fijo). Esto conduce a una serie de limitaciones (por ejemplo, la página
no crecerá/reducirá automáticamente de la misma manera que lo hará uno orientado verticalmente), por lo que
Ethereal hace dos cosas para solucionar este problema:

- Toda la página se compone de elementos de "panel", a cada uno de los cuales se le puede asignar un
modificador de "tamaño" opcional (que satisface el requisito de ancho fijo).

- Para paneles que no utilizan un modificador de tamaño, elementos individuales que contienen *dentro*
A ellos (por ejemplo, una columna) se les puede asignar un modificador "span" para darles un ancho fijo.
en su lugar (satisfaciendo también el requisito de ancho fijo).

Otra peculiaridad divertida de las páginas de desplazamiento lateral es cómo implementar páginas horizontales.
desplazarse *sin* recurrir al uso de la barra de desplazamiento horizontal (generalmente fea).
Ethereal hace esto de CUATRO (!) maneras:

- Arrastrar: los usuarios pueden simplemente hacer clic y arrastrar la página hacia la izquierda o hacia la derecha para desplazarla.
Esto funciona exactamente como cabría esperar e incluso tiene un agradable efecto de "impulso posterior al desplazamiento".

- Rueda de desplazamiento: Ethereal modifica* el comportamiento de la rueda de desplazamiento para traducirla verticalmente.
desplazarse hacia el desplazamiento horizontal, lo que permite al usuario utilizar la rueda de desplazamiento
o trackpad para desplazarse por la página (el último de los cuales conserva la capacidad de desplazarse horizontalmente
desplácese normalmente, para que nada cambie allí).

* Un agradecimiento especial a @miorel + @pieterv de Facebook por "normalizeWheel()" :)

- Zonas de desplazamiento: los usuarios pueden colocar el cursor del mouse en los bordes izquierdo o derecho de la página
para desplazarse automáticamente en cualquier dirección.

- Atajos de teclado: Finalmente, los usuarios pueden simplemente usar las flechas izquierda/derecha, subir/abajo de página,
inicio/fin y la barra espaciadora para desplazarse por la página.

Tenga en cuenta que cualquiera (o todas) de estas funciones de asistencia de desplazamiento se pueden desactivar (y en algunos casos
casos personalizados). Consulte la parte superior de activos/js/main.js para obtener más información.


	Modificadores de intervalo
===============

Los modificadores de extensión son simplemente clases que dan a los elementos un ancho fijo, cuyo tamaño
está determinado por el "valor unitario" asociado con el modificador (por ejemplo, "span-3" significa
"abarca 3 unidades"). Estos tamaños están en unidades "rem" cuando se usan dentro de paneles que no
use un modificador de tamaño y en unidades porcentuales cuando se use dentro de paneles que lo hagan.

Ethereal incluye modificadores de intervalo que van desde 0,25 unidades ("span-0-25") hasta 10 unidades
("lapso-10"). Aquí hay una lista parcial:

span-0-25 Span 0,25 unidades.
span-0-5 Span 0,5 unidades.
span-0-75 Span 0,75 unidades.
span-1 Span 1 unidad.
span-1-25 Span 1,25 unidades.
span-1-5 Amplitud 1,5 unidades.
span-1-75 Span 1,75 unidades.
...
span-9 Abarca 9 unidades.
span-9-25 Span 9,25 unidades.
span-9-5 Span 9,5 unidades.
span-9-75 Span 9,75 unidades.
span-10 Abarca 10 unidades.


	Elementos principales
===============

La mayoría de los elementos de Ethereal son más o menos lo que cabría esperar, pero hay algunos
de los "importantes" que merecen un poco más de explicación:


Panel
------

El componente principal de Ethereal.

HTML

<section class="panel (modificador de tamaño) (modificador de color)">
<div class="introducción (modificador de color)">
(contenido de introducción)
</div>
<div class="inner (modificadores internos) (modificador de color)">
(contenido interno)
</div>
</sección>

Nota: Se puede excluir todo el elemento secundario "introducción".
Nota: Puede tener tantos elementos secundarios "introductorios" e "internos" como desee.

Modificadores

Tamaño

pequeño Utilice tamaño pequeño.
mediano Utilice tamaño mediano.
grande Utilice tamaño grande.

Color

color0 Utilice el color de fondo 0 (degradado).
color1 Utilice el color de fondo 1.
color2 Utilice el color de fondo 2.
color3 Utilice el color de fondo 3.
color4 Utilice el color de fondo 4.
color1-alt Utiliza el color de fondo 1 (alt).
color2-alt Utilice el color de fondo 2 (alt).
color3-alt Utilice el color de fondo 3 (alt).
color4-alt Utilice el color de fondo 4 (alt).

Interno

columnas Divide los elementos secundarios en columnas.
alineado Cuando se usa con "columnas", alinea el contenido con la parte superior del panel.
dividido Cuando se usa con "columnas", separa cada columna con una línea vertical.

Ejemplos

Aquí hay un ejemplo muy básico:

<sección clase="panel color medio0">
<div clase="introducción">
<h2 class="mayor">Panel</h2>
<p>Solo un panel genérico.</p>
</div>
<div class="interior">
<p>Lorem ipsum dolor sit amet.</p>
</div>
</sección>

Y aquí hay un ejemplo más avanzado usando columnas y *sin* modificador de tamaño:

<sección clase="color del panel2">
<div clase="introducción">
<h2 class="mayor">Panel</h2>
<p>Solo un panel genérico.</p>
</div>
<div class="columnas internas">
<div clase="span-4">
<p>Esta columna tiene 4 unidades de ancho.</p>
</div>
<div clase="span-3">
<p>Esta columna tiene 3 unidades de ancho.</p>
</div>
<div clase="span-2">
<p>Esta columna tiene 2 unidades de ancho.</p>
</div>
</div>
</sección>

Nota: El elemento secundario "introducción" ya tiene un ancho fijo, por lo que se debe usar un modificador de extensión.
no es necesario.


		Panel (banner)
--------------

La variante "Banner" de un panel normal.

HTML

<section class="banner del panel (modificador de tamaño) (modificador de color) (modificador de orientación)">
<div class="contenido (modificador de color)">
(contenido)
</div>
<div class="imagen (modificadores de imagen)" data-position="(modificador de posición de imagen)">
<img src="(URL de la imagen)" alt="" />
</div>
</sección>

Modificadores

Orientación

left Contenido a la izquierda, imagen a la derecha.
right Contenido a la derecha, imagen a la izquierda.

Imagen

filtrado Aplica un filtro de degradado a la imagen.
teñido Aplica un filtro de tinte a la imagen.

Posición de la imagen (requerido)

arriba a la izquierda Coloque la imagen en la esquina superior izquierda.
top Coloque la imagen a lo largo del borde superior.
arriba a la derecha Coloque la imagen en la esquina superior derecha.
derecha Coloque la imagen a lo largo del borde derecho.
abajo a la derecha Coloque la imagen en la esquina inferior derecha.
inferior Coloque la imagen a lo largo del borde inferior.
abajo a la izquierda Coloque la imagen en la esquina inferior izquierda.
izquierda Coloque la imagen a lo largo del borde izquierdo.
centro Coloque la imagen en el centro.

Ejemplo

<section class="banner del panel medio derecho">
<div class="color de contenido0">
<h1>Banner</h1>
<p>Lorem ipsum dolor sit amet.</p>
</div>
<div class="imagen" posición-datos="centro">
<img src="/ruta/a/imagen.jpg" alt="" />
</div>
</sección>


Panel (enfoque)
-----------------

La variante "Spotlight" de un panel normal.

HTML

<section class="panel reflector (modificador de tamaño) (modificador de orientación)">
<div class="contenido (modificador de extensión)">
(contenido)
</div>
<div class="imagen (modificadores de imagen)" data-position="(modificador de posición de imagen)">
<img src="(URL de la imagen)" alt="" />
</div>
</sección>

Modificadores

Orientación

left Contenido a la izquierda.
contenido derecho a la derecha.

Imagen

filtrado Aplica un filtro de degradado a la imagen.
teñido Aplica un filtro de tinte a la imagen.

Posición de la imagen (requerido)

arriba a la izquierda Coloque la imagen en la esquina superior izquierda.
top Coloque la imagen a lo largo del borde superior.
arriba a la derecha Coloque la imagen en la esquina superior derecha.
derecha Coloque la imagen a lo largo del borde derecho.
abajo a la derecha Coloque la imagen en la esquina inferior derecha.
inferior Coloque la imagen a lo largo del borde inferior.
abajo a la izquierda Coloque la imagen en la esquina inferior izquierda.
izquierda Coloque la imagen a lo largo del borde izquierdo.
centro Coloque la imagen en el centro.

Ejemplo

<section class="panel reflector grande derecha">
<div clase="contenido">
<h1>Enfoque</h1>
<p>Lorem ipsum dolor sit amet.</p>
</div>
<div class="imagen" posición-datos="centro">
<img src="/ruta/a/imagen.jpg" alt="" />
</div>
</sección>


Galería
-------

Una galería habilitada para cajas de luz.

HTML

<div clase="galería">
<a href="(URL de imagen completa)" class="imagen (modificadores de imagen) (modificador de extensión)" data-position="(modificador de posición de imagen)">
<img src="(URL de la imagen en miniatura)" alt="" />
</a>
<a href="(URL de imagen completa)" class="imagen (modificadores de imagen) (modificador de extensión)" data-position="(modificador de posición de imagen)">
<img src="(URL de la imagen en miniatura)" alt="" />
</a>
<a href="(URL de imagen completa)" class="imagen (modificadores de imagen) (modificador de extensión)" data-position="(modificador de posición de imagen)">
<img src="(URL de la imagen en miniatura)" alt="" />
</a>
<div class="grupo (modificador de intervalo)">
<a href="(URL de imagen completa)" class="imagen (modificadores de imagen) (modificador de extensión)" data-position="(modificador de posición de imagen)">
<img src="(URL de la imagen en miniatura)" alt="" />
</a>
<a href="(URL de imagen completa)" class="imagen (modificadores de imagen) (modificador de extensión)" data-position="(modificador de posición de imagen)">
<img src="(URL de la imagen en miniatura)" alt="" />
</a>
<a href="(URL de imagen completa)" class="imagen (modificadores de imagen) (modificador de extensión)" data-position="(modificador de posición de imagen)">
<img src="(URL de la imagen en miniatura)" alt="" />
</a>
<a href="(URL de imagen completa)" class="imagen (modificadores de imagen) (modificador de extensión)" data-position="(modificador de posición de imagen)">
<img src="(URL de la imagen en miniatura)" alt="" />
</a>
...
</div>
...
</div>

Nota: El elemento "grupo" crea un grupo de imágenes de dos filas. Las imágenes dentro de este grupo
pasan automáticamente a la siguiente fila cuando exceden su ancho (según lo definido por su modificador de extensión).
Puedes tener tantos grupos en una galería como quieras.

Modificadores

Imagen

filtrado Aplica un filtro de degradado a la imagen.
teñido Aplica un filtro de tinte a la imagen.

Posición de la imagen (requerido)

arriba a la izquierda Coloque la imagen en la esquina superior izquierda.
arriba Coloque la imagen a lo largo del e borde superior.
arriba a la derecha Coloque la imagen en la esquina superior derecha.
derecha Coloque la imagen a lo largo del borde derecho.
abajo a la derecha Coloque la imagen en la esquina inferior derecha.
inferior Coloque la imagen a lo largo del borde inferior.
abajo a la izquierda Coloque la imagen en la esquina inferior izquierda.
izquierda Coloque la imagen a lo largo del borde izquierdo.
centro Coloque la imagen en el centro.

Ejemplo

<div clase="galería">
<a href="/images/thumbnails/01.jpg" class="imagen filtrada span-2" data-position="center">
<img src="/images/fulls/01.jpg" alt="" />
</a>
<a href="/images/thumbnails/02.jpg" class="imagen filtrada entre 4" data-position="center">
<img src="/images/fulls/02.jpg" alt="" />
</a>
<div class="grupo span-4">
<a href="/images/thumbnails/03.jpg" class="imagen filtrada span-2" data-position="center">
<img src="/images/fulls/03.jpg" alt="" />
</a>
<a href="/images/thumbnails/04.jpg" class="imagen filtrada span-2" data-position="center">
<img src="/images/fulls/04.jpg" alt="" />
</a>
<a href="/images/thumbnails/05.jpg" class="imagen filtrada span-2" data-position="center">
<img src="/images/fulls/05.jpg" alt="" />
</a>
<a href="/images/thumbnails/06.jpg" class="imagen filtrada span-2" data-position="center">
<img src="/images/fulls/06.jpg" alt="" />
</a>
</div>
</div>


Créditos:

Imágenes de demostración:
Unsplash (unsplash.com)

Iconos:
Fuente impresionante (fortawesome.github.com/Font-Awesome)

Otro:
jQuery (jquery.com)
Varios. Funciones descaradas (@HugoGiraudel)
normalizeWheel (@miorel + @pieterv de Facebook)
Skel (skel.io)