# Instrucciones del Proyecto

Bienvenido/a — este archivo genera una página con las instrucciones visibles para el proyecto.

---

## Objetivo

Proveer una guía clara y accesible para entender, ejecutar y contribuir al proyecto "Transparencia Fácil".

## Contenido de esta página

- **Resumen del proyecto**: qué hace y a quién va dirigido.
- **Estructura del repositorio**: dónde encontrar archivos importantes.
- **Cómo ejecutar**: pasos mínimos para ver o probar el proyecto localmente.
- **Cómo contribuir**: pautas rápidas para colaborar.
- **Contacto**: a quién dirigirse si hay dudas.

## Resumen del proyecto

Este repositorio contiene el trabajo final del curso de programación para el proyecto "Transparencia Fácil". El propósito es facilitar el acceso y comprensión de datos y procesos relevantes para la transparencia pública.

## Estructura del repositorio (resumen)

- `.github/instructions/`: documentación e instrucciones (este archivo).
- `src/` o `app/` (si existe): código fuente principal.
- `docs/` (si existe): documentación adicional y recursos.
- `README.md`: introducción y enlaces rápidos.

Si algún directorio no existe, busca archivos README o cualquier archivo con instrucciones en la raíz del proyecto.

## Cómo ejecutar (ejemplo genérico)

1. Clona el repositorio o descarga los archivos.

2. Abre una terminal en la carpeta del proyecto.

3. Si el proyecto usa Node.js y tiene `package.json`:

```
# Instala dependencias
npm install

# Ejecuta la aplicación en modo desarrollo
npm start
```

4. Si el proyecto es en Python y tiene `requirements.txt`:

```
# Crea un entorno virtual (PowerShell)
python -m venv .venv; .\.venv\Scripts\Activate.ps1
pip install -r requirements.txt

# Ejecuta la aplicación
python main.py
```

5. Si no estás seguro, abre `README.md` en la raíz del repositorio — normalmente contiene instrucciones específicas.

## Cómo contribuir (rápido)

1. Crea una rama nueva con un nombre descriptivo.
2. Haz cambios pequeños y claros; agrega pruebas o explicaciones cuando apliquen.
3. Abre un Pull Request con descripción y pasos para probar los cambios.

## Notas sobre accesibilidad y visibilidad

- Este archivo está escrito en Markdown para que GitHub muestre las instrucciones como página legible.
- Si prefieres una página HTML lista para desplegar, puedo generar una versión `index.html` con estilos básicos.

## Contacto

Si tienes preguntas sobre el contenido o necesitas que adapte las instrucciones a un entorno específico, contacta a los mantenedores del repo o responde a este ticket.

---

Archivo: `.github/instructions/proyect-context.instructions.md` — actualizado para mostrar instrucciones visibles.
TransparenciaFacilCL Tailwind CSS - Instrucciones para Agente IA
Desarrollar una sopa de letras interactiva basada en los contenidos publicados en el sitio TransparenciaFacilCL (WordPress). El objetivo es construir un recurso lúdico y educativo que tome términos, conceptos y categorías del sitio y los transforme en un juego navegable.
El desarrollo se realizará en HTML y Tailwind CSS, apoyándonos en agentes de inteligencia artificial integrados en VS Code para agilizar la generación de código, la organización del layout y la automatización de tareas.
Básate en estas librerías de javascript para la contrucción de lo siguente:


Archivo index.html

Dentro del archivo index.html crearemos la estructura de la sopa de letras. Además añadiremos jquery y los otros dos archivos js que vamos a crear (wordfind y wordfindgame). En este archivo añadiremos un array con las palabras que los usuarios tendremos que buscar (no les han puesto acentos, para hacerlo más complicado en la sopa de letras). También vamos a crear dos funciones, con las cuales podremos resolver la sopa de letras o reiniciarla. A estas funciones accederemos gracias a los dos botones que se han colocado en la parte inferior de la página.
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Sopa de letras - JavaScript</title>
    <link rel="stylesheet" href="style.css" type="text/css" media="all" />
        <!-- Dependencias -->
    <script src="https://code.jquery.com/jquery-2.2.4.min.js" crossorigin="anonymous"></script>
    <script src="wordfind.js"></script>
    <script src="wordfindgame.js"></script>
</head>

<body>
    <!-- Estructura de la sopa de letras-->
    <div class="titulo">Sopa de Letras</div>
    <input type="button" id="BTNresolver" value="Resolver sopa de letras" />
    <input type="button" value="Reiniciar la sopa de letras" id="BTNrefresh">
    <div id="contenedor"></div>
    <div id="palabras-sopadeletras"></div>

    <!-- Construcción de la sopa de letras -->
    <script>
        // Array con las palabras que el usuario debe buscar
        var palabras = ['pie', 'localizar', 'coche',
            'culo', 'pelo', 'formula',
            'resfriado', 'perro', 'pescador',
            'repartidor', 'programador', 'velocimetro',
            'contador', 'salinidad', 'tabaco',
            'oso', 'ceniza', 'electricidad',
            'buho', 'frecuencia', 'entreunosyceros',
            'onanismo', 'osmosis', 'zapato'
        ];

        // Comienza un juego de palabras
        var sopaLetras = wordfindgame.create(palabras, '#contenedor', '#palabras-sopadeletras');

        // Función para resolver la sopa de petras             
        $("#BTNresolver").click(function () {
            var resultado = wordfindgame.solve(sopaLetras, palabras);
            console.log(resultado);
        });

        // Función para reiniciar la sopa de letras
        $("#BTNrefresh").click(function () {
            window.location.href = window.location.href;
        });
    </script>
</body>

</html>
wordfindgame.js
/**
* wordfindgame.js
* Script to create the GUI
* Wordfindgame.js
* (c) 2012 Bill, BunKat LLC.
* Wordfind is freely distributable under the MIT license.
* For all details and documentation: http://github.com/bunkat/wordfind
*/
!function(e,t,n){"use strict";var r=function(){var r,o,a,l=function(e,n){for(var r="",o=0,a=n.length;a>o;o++){var l=n[o];r+="<div>";for(var u=0,s=l.length;s>u;u++)r+='<button class="letra" x="'+u+'" y="'+o+'">',r+=l[u]||"&nbsp;",r+="</button>";r+="</div>"}t(e).html(r)},u=function(e,n){for(var r="<ul>",o=0,a=n.length;a>o;o++){var l=n[o];r+='<li class="word '+l+'">'+l}r+="</ul>",t(e).html(r)},s=[],i="",d=function(){t(this).addClass("selected"),o=this,s.push(this),i=t(this).text()},c=function(e){if(o){var n=s[s.length-1];if(n!=e){for(var r,l=0,u=s.length;u>l;l++)if(s[l]==e){r=l+1;break}for(;r<s.length;)t(s[s.length-1]).removeClass("selected"),s.splice(r,1),i=i.substr(0,i.length-1);var d=p(t(o).attr("x")-0,t(o).attr("y")-0,t(e).attr("x")-0,t(e).attr("y")-0);d&&(s=[o],i=t(o).text(),n!==o&&(t(n).removeClass("selected"),n=o),a=d);var c=p(t(n).attr("x")-0,t(n).attr("y")-0,t(e).attr("x")-0,t(e).attr("y")-0);c&&(a&&a!==c||(a=c,h(e)))}}},f=function(t){var n=t.originalEvent.touches[0].pageX,r=t.originalEvent.touches[0].pageY,o=e.elementFromPoint(n,r);c(o)},v=function(){c(this)},h=function(e){for(var n=0,o=r.length;o>n;n++)if(0===r[n].indexOf(i+t(e).text())){t(e).addClass("selected"),s.push(e),i+=t(e).text();break}},z=function(){for(var e=0,n=r.length;n>e;e++)r[e]===i&&(t(".selected").addClass("found"),r.splice(e,1),t("."+i).addClass("palabraEncontrada")),0===r.length&&t(".letra").addClass("complete");t(".selected").removeClass("selected"),o=null,s=[],i="",a=null},p=function(e,t,r,o){for(var a in n.orientations){var l=n.orientations[a],u=l(e,t,1);if(u.x===r&&u.y===o)return a}return null};return{create:function(e,o,a,s){r=e.slice(0).sort();var i=n.newPuzzle(e,s);return l(o,i),u(a,r),window.navigator.msPointerEnabled?(t(".letra").on("MSPointerDown",d),t(".letra").on("MSPointerOver",c),t(".letra").on("MSPointerUp",z)):(t(".letra").mousedown(d),t(".letra").mouseenter(v),t(".letra").mouseup(z),t(".letra").on("touchstart",d),t(".letra").on("touchmove",f),t(".letra").on("touchend",z)),i},solve:function(e,r){for(var o=n.solve(e,r).found,a=0,l=o.length;l>a;a++){var u=o[a].word,s=o[a].orientation,i=o[a].x,d=o[a].y,c=n.orientations[s];if(!t("."+u).hasClass("palabraEncontrada")){for(var f=0,v=u.length;v>f;f++){var h=c(i,d,f);t('[x="'+h.x+'"][y="'+h.y+'"]').addClass("solved")}t("."+u).addClass("palabraEncontrada")}}}}};window.wordfindgame=r()}(document,jQuery,wordfind);


Archivo style.css
Dentro del archivo style.css vamos a añadir algunas reglas CSS para darle un poco de estilo a la sopa de letras. Cada cual que lo mejore o lo cambie a su gusto. Bien es cierto que no se han añadido reglas para dispositivos móviles, por lo que se deduce que este ejemplo está pensado para funcionar en navegadores web desde una pantalla decente.

Aquí no se hace nada más que eso, por lo que dentro del archivo solo hay que pegar el siguiente código:


body {
    background-color: #000000;
    color: #fff;
    display: flex;
    justify-content: center;
    align-items: center;
    max-height: 100vh;
}

/* Contenedor de la sopa de letras */

#contenedor {
    border: 1px solid rgb(0, 17, 255);
    padding: 20px;
    float: left;
    margin: 150px 20px;
}

#contenedor div {
    width: 100%;
    margin: 0 auto;
}

/* Estilo para cada cuadrado de la sopa de letras */

#contenedor .letra {
    height: 30px;
    width: 30px;
    text-transform: uppercase;
    background-color: white;
    border: 0;
    font: 1em sans-serif;
}

/* Colores cuando se selecciona un cuadrado */

#contenedor .selected {
    background-color: rgb(8, 179, 2);
}

#contenedor:hover .selected:hover {
    background-color: rgb(145, 255, 0);
    font-weight: bold;
}

#contenedor>div>button:hover {
    background-color: rgb(145, 255, 0);
    font-weight: bold;
}

/* Indica que la letra es parte de una palabra que se ha encontrado */

#contenedor .found {
    background-color: #c0c0c0;
    color: white;
    border: 1px solid black;
    font-weight: bold;
    text-shadow: 0px 2px 3px #000;
}

#contenedor .found:hover {
    background-color: rgb(145, 255, 0);
    font-weight: bold;
}

/* Colores de palabras no encontradas cuando se pulsa el botón Resolver sopa de letras*/

#contenedor .solved {
    background-color: purple;
    color: white;
}

/* Cambio de color de fondo cuando se encuentras todas las palabras*/

#contenedor .complete {
    background-color: green;
}

/**
* Estilos para la lista de palabras
*/

#palabras-sopadeletras {
    padding-top: 20px;
    -moz-column-count: 2;
    -moz-column-gap: 20px;
    -webkit-column-count: 2;
    -webkit-column-gap: 20px;
    column-count: 2;
    column-gap: 20px;
    width: 300px;
}

#palabras-sopadeletras ul {
    list-style-type: none;
}

#palabras-sopadeletras li {
    padding: 3px 0;
    font: 1em sans-serif;
}

/*Indica que la palabra ha sido encontrada en la lista */

#palabras-sopadeletras .palabraEncontrada {
    text-decoration: line-through;
    color: rgb(255, 0, 0);
}

/**
*  Estilos para el botón
*/

#BTNrefresh {
    position: absolute;
    bottom: 0em;
}

#BTNresolver {
    bottom: 3em;
    position: absolute;
}

/* Título */

.titulo {
    display: inline-block;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    padding: 10px;
    border: none;
    font: normal 48px/normal "Warnes", Helvetica, sans-serif;
    color: rgba(255, 255, 255, 1);
    text-decoration: normal;
    text-align: center;
    -o-text-overflow: clip;
    text-overflow: clip;
    white-space: pre;
    text-shadow: 0 0 10px rgba(255, 255, 255, 1), 0 0 20px rgba(255, 255, 255, 1), 0 0 30px rgba(255, 255, 255, 1), 0 0 40px #ff00de, 0 0 70px #ff00de, 0 0 80px #ff00de, 0 0 100px #ff00de;
    -webkit-transition: all 200ms cubic-bezier(0.42, 0, 0.58, 1);
    -moz-transition: all 200ms cubic-bezier(0.42, 0, 0.58, 1);
    -o-transition: all 200ms cubic-bezier(0.42, 0, 0.58, 1);
    transition: all 200ms cubic-bezier(0.42, 0, 0.58, 1);
    position: absolute;
    top: 1em;
}

.titulo:hover {
    text-shadow: 0 0 10px rgba(255, 255, 255, 1), 0 0 20px rgba(255, 255, 255, 1), 0 0 30px rgba(255, 255, 255, 1), 0 0 40px #00ffff, 0 0 70px #00ffff, 0 0 80px #00ffff, 0 0 100px #00ffff;
}


wordfine.js
// wordfind.js
/**
* Wordfind.js
* (c) 2012 Bill, BunKat LLC.
* Wordfind is freely distributable under the MIT license.
* @documentation http://github.com/bunkat/wordfind
*/
(function(){"use strict";var n=function(){var n="abcdefghijklmnoprstuvwyz",r=["horizontal","horizontalBack","vertical","verticalUp","diagonal","diagonalUp","diagonalBack","diagonalUpBack"],t={horizontal:function(n,r,t){return{x:n+t,y:r}},horizontalBack:function(n,r,t){return{x:n-t,y:r}},vertical:function(n,r,t){return{x:n,y:r+t}},verticalUp:function(n,r,t){return{x:n,y:r-t}},diagonal:function(n,r,t){return{x:n+t,y:r+t}},diagonalBack:function(n,r,t){return{x:n-t,y:r+t}},diagonalUp:function(n,r,t){return{x:n+t,y:r-t}},diagonalUpBack:function(n,r,t){return{x:n-t,y:r-t}}},o={horizontal:function(n,r,t,o,e){return o>=n+e},horizontalBack:function(n,r,t,o,e){return n+1>=e},vertical:function(n,r,t,o,e){return t>=r+e},verticalUp:function(n,r,t,o,e){return r+1>=e},diagonal:function(n,r,t,o,e){return o>=n+e&&t>=r+e},diagonalBack:function(n,r,t,o,e){return n+1>=e&&t>=r+e},diagonalUp:function(n,r,t,o,e){return o>=n+e&&r+1>=e},diagonalUpBack:function(n,r,t,o,e){return n+1>=e&&r+1>=e}},e={horizontal:function(n,r,t){return{x:0,y:r+1}},horizontalBack:function(n,r,t){return{x:t-1,y:r}},vertical:function(n,r,t){return{x:0,y:r+100}},verticalUp:function(n,r,t){return{x:0,y:t-1}},diagonal:function(n,r,t){return{x:0,y:r+1}},diagonalBack:function(n,r,t){return{x:t-1,y:n>=t-1?r+1:r}},diagonalUp:function(n,r,t){return{x:0,y:t-1>r?t-1:r+1}},diagonalUpBack:function(n,r,t){return{x:t-1,y:n>=t-1?r+1:r}}},i=function(n,r){var t,o,e,i=[];for(t=0;t<r.height;t++)for(i.push([]),o=0;o<r.width;o++)i[t].push("");for(t=0,e=n.length;e>t;t++)if(!a(i,r,n[t]))return null;return i},a=function(n,r,o){var e=l(n,r,o);if(0===e.length)return!1;var i=e[Math.floor(Math.random()*e.length)];return c(n,o,i.x,i.y,t[i.orientation]),!0},l=function(n,r,i){for(var a=[],l=r.height,c=r.width,h=i.length,g=0,v=0,p=r.orientations.length;p>v;v++)for(var d=r.orientations[v],s=o[d],x=t[d],y=e[d],k=0,B=0;l>B;)if(s(k,B,l,c,h)){var w=u(i,n,k,B,x);(w>=g||!r.preferOverlap&&w>-1)&&(g=w,a.push({x:k,y:B,orientation:d,overlap:w})),k++,k>=c&&(k=0,B++)}else{var U=y(k,B,h);k=U.x,B=U.y}return r.preferOverlap?f(a,g):a},u=function(n,r,t,o,e){for(var i=0,a=0,l=n.length;l>a;a++){var u=e(t,o,a),f=r[u.y][u.x];if(f===n[a])i++;else if(""!==f)return-1}return i},f=function(n,r){for(var t=[],o=0,e=n.length;e>o;o++)n[o].overlap>=r&&t.push(n[o]);return t},c=function(n,r,t,o,e){for(var i=0,a=r.length;a>i;i++){var l=e(t,o,i);n[l.y][l.x]=r[i]}};return{validOrientations:r,orientations:t,newPuzzle:function(n,t){var o,e,a=0,l=t||{};o=n.slice(0).sort(function(n,r){return n.length<r.length?1:0});for(var u={height:l.height||o[0].length,width:l.width||o[0].length,orientations:l.orientations||r,fillBlanks:void 0!==l.fillBlanks?l.fillBlanks:!0,maxAttempts:l.maxAttempts||3,preferOverlap:void 0!==l.preferOverlap?l.preferOverlap:!0};!e;){for(;!e&&a++<u.maxAttempts;)e=i(o,u);e||(u.height++,u.width++,a=0)}return u.fillBlanks&&this.fillBlanks(e,u),e},fillBlanks:function(r){for(var t=0,o=r.length;o>t;t++)for(var e=r[t],i=0,a=e.length;a>i;i++)if(!r[t][i]){var l=Math.floor(Math.random()*n.length);r[t][i]=n[l]}},solve:function(n,t){for(var o={height:n.length,width:n[0].length,orientations:r,preferOverlap:!0},e=[],i=[],a=0,u=t.length;u>a;a++){var f=t[a],c=l(n,o,f);c.length>0&&c[0].overlap===f.length?(c[0].word=f,e.push(c[0])):i.push(f)}return{found:e,notFound:i}},print:function(n){for(var r="",t=0,o=n.length;o>t;t++){for(var e=n[t],i=0,a=e.length;a>i;i++)r+=(""===e[i]?" ":e[i])+" ";r+="\n"}return console.log(r),r}}},r="undefined"!=typeof exports&&null!==exports?exports:window;r.wordfind=n()}).call(this);






🎯 Propósito del Proyecto
Este es un playground educativo donde los usuarios pueden:
Aprender mediante el juego
Leer ciertas preguntas que tengan que ver con transparencia en Chile y que se respondan con una sola palabra
Encontrar esas palabras dentro de la sopa de letras

📋 Reglas Generales del Proyecto
Estructura del Proyecto
NUNCA modifiques package.json, tailwind.config.js o archivos de configuración sin permiso explícito
NUNCA ejecutes npm install o npm run dev - el servidor ya está corriendo
Todos los cambios deben hacerse en index.html o archivos en assets/
El archivo principal de trabajo es index.html
Archivos Clave
index.html              → Archivo HTML principal (AQUÍ trabajamos)
assets/css/base.css    → Input de Tailwind (NO modificar)
assets/css/styles.css  → Output compilado (NO modificar manualmente)
assets/js/scripts.js   → JavaScript vanilla opcional
tailwind.config.js     → Configuración de Tailwind (NO modificar sin permiso)



🎨 Reglas de Estilizado con Tailwind CSS
Uso Obligatorio de Tailwind
TODOS los estilos DEBEN usar clases utilitarias de Tailwind CSS
PROHIBIDO usar:
Estilos inline con atributo style="..."
CSS personalizado en archivos separados
Otros frameworks CSS (Bootstrap, Bulma, etc.)
Tailwind ya está configurado y funcionando correctamente
Ejemplos Correctos vs Incorrectos
❌ INCORRECTO:
<div style="color: blue; margin: 20px;">Texto</div>
<div class="mi-clase-custom">Texto</div>
✅ CORRECTO:
<div class="text-blue-500 m-5">Texto</div>
<div class="flex items-center justify-between p-4 bg-gray-100 rounded-lg">Texto</div>
Clases de Tailwind Recomendadas para Estudiantes
Layout: flex, grid, container, mx-auto
Spacing: p-4, m-8, space-y-4, gap-6
Colors: bg-blue-500, text-gray-800, border-red-300
Typography: text-xl, font-bold, leading-relaxed
Responsive: md:flex, lg:grid-cols-3, sm:text-sm
Effects: hover:bg-blue-600, shadow-lg, rounded-xl, transition-all

🏗️ Reglas de HTML Semántico
Estructura Semántica Obligatoria
Usa HTML5 semántico siempre:
<header>, <nav>, <main>, <section>, <article>, <aside>, <footer>
NO uses <div> cuando exista un elemento semántico apropiado
Estructura SEO-friendly desde el inicio
Ejemplos de Estructura Correcta
❌ INCORRECTO:
<div class="header">
  <div class="nav">
    <div>Elemento 1</div>
    <div>Elemento 2</div>
  </div>
</div>
✅ CORRECTO:
<header class="bg-white shadow-md">
  <nav class="container mx-auto px-4 py-3">
    <ul class="flex gap-4">
      <li><a href="#" class="hover:text-blue-600">Elemento 1</a></li>
      <li><a href="#" class="hover:text-blue-600">Elemento 2</a></li>
    </ul>
  </nav>
</header>
Listas para Contenido Repetido
Usa <ul>, <ol>, <li> para elementos repetidos
NUNCA uses múltiples <div> para listas de items
Ejemplos: menús de navegación, tarjetas de productos, listas de características

♿ Accesibilidad (A11y)
Reglas Obligatorias
Atributo lang: El HTML tiene lang="es_CL" configurado
Atributos ARIA cuando sea necesario:
aria-label para iconos sin texto
aria-expanded para elementos colapsables
role para componentes complejos
Alt text obligatorio en todas las <img>
Contraste de color adecuado (usa dark:text-gray-800, no gray-400 en fondos claros)
Navegación por teclado: todos los elementos interactivos deben ser accesibles
Ejemplo Accesible
<button 
  aria-label="Abrir menú de navegación" 
  class="p-2 hover:bg-gray-100 rounded-md focus:ring-2 focus:ring-blue-500">
  <svg class="w-6 h-6" aria-hidden="true">...</svg>
</button>

📱 Responsive Design
Mobile-First Approach
Diseña primero para móvil, luego escala con breakpoints
Usa los prefijos de Tailwind: sm:, md:, lg:, xl:, 2xl:
Prueba todos los diseños en diferentes tamaños
Breakpoints de Tailwind
sm:  640px   → Teléfonos grandes
md:  768px   → Tablets
lg:  1024px  → Laptops
xl:  1280px  → Desktops
2xl: 1536px  → Pantallas grandes


Ejemplo Responsive
<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-4">
  <div class="p-4 bg-white rounded-lg shadow">Card 1</div>
  <div class="p-4 bg-white rounded-lg shadow">Card 2</div>
  <div class="p-4 bg-white rounded-lg shadow">Card 3</div>
</div>

⚡ Performance y Optimización
Objetivos de Performance
Meta: 100/100 en Google PageSpeed Insights (Mobile & Desktop)
Minimiza JavaScript del lado del cliente
Usa rendering del lado del servidor cuando sea posible
Fuentes Tipográficas
USA paquetes @fontsource para Google Fonts
NO USES el CDN de Google Fonts (<link> a fonts.googleapis.com)
PREFIERE fuentes variables cuando estén disponibles
Configura las fuentes en tailwind.config.js bajo fontFamily
Proceso para Agregar Fuentes
# 1. Instalar la fuente
npm install @fontsource-variable/inter

# 2. Importar en base.css
# @import '@fontsource-variable/inter';

# 3. Configurar en tailwind.config.js
# fontFamily: { sans: ['Inter Variable', 'sans-serif'] }

💻 JavaScript
Reglas de JavaScript
Solo JavaScript vanilla está permitido
NO uses frameworks/librerías (React, Vue, jQuery, etc.) sin permiso explícito
El archivo de trabajo es assets/js/scripts.js
Mantén el JavaScript mínimo y progresivo (mejora progresiva)
Ejemplo de JavaScript Permitido
// assets/js/scripts.js
document.addEventListener('DOMContentLoaded', () => {
  const button = document.querySelector('#toggle-menu');
  button?.addEventListener('click', () => {
    // Lógica simple
  });
});

