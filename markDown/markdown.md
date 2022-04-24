# Básicos - Markdown

## Tabla de contenidos {id='indice'}

- [¿Qué es Markdown?](#id1)
- [¿Por qué usar Markdown?](#id2)
- [¿Como funciona?](#id3)
- [¿Para qué sirve Markdown?](#id4)
- [Sabores de Markdown](#id5)
- [Sintaxis básica](#id6)

## ¿Qué es Markdown? {id='id1'}

***Markdown*** es un lenguaje de marcado ligero que puede usar para agregar elementos de formato a documentos de texto sin formato. Fue Creado por John Gruber en 2004.

El objetivo principal del diseño de la sintaxis de formato de Markdown es hacer que sea lo más legible posible. La idea es que un documento con formato de Markdown se pueda publicar tal cual, como texto sin formato, sin que parezca que ha sido marcado con etiquetas o instrucciones de formato.

<div style="text-align: right"> 

  [:arrow_up:](#indice)

</div>


## ¿Por qué usar Markdown? {id='id2'}

- Markdown se puede utilizar ***para crear sitios web, documentos, notas, libros, presentaciones, mensajes de correo electrónico y documentación técnica***.

- Markdown ***es portátil***. Los archivos que contienen texto con formato Markdown se pueden abrir con prácticamente cualquier aplicación. 

- Markdown ***es independiente de la plataforma***. Puede crear texto con formato Markdown en cualquier dispositivo que ejecute cualquier sistema operativo.

- Markdown ***es una prueba de futuro***. Incluso si la aplicación que está usando deja de funcionar en algún momento en el futuro, aún podrá leer su texto con formato Markdown usando una aplicación de edición de texto.

- Markdown ***está en todas partes***. Los sitios web como Reddit y GitHub son compatibles con Markdown, y muchas aplicaciones de escritorio y basadas en la web lo admiten.

<div style="text-align: right"> 

  [:arrow_up:](#indice)

</div>

## ¿Como funciona? {id='id3'}

Las aplicaciones de Markdown usan un procesador de Markdown (también conocido como "analizador" o "implementación") para tomar el texto con formato de Markdown y enviarlo a formato HTML. En ese momento, su documento puede verse en un navegador web o combinarse con una hoja de estilo e imprimirse. Puede ver una representación visual de este proceso a continuación.

![Cómo funciona?](./assets/images/markdown_1.png) 

<div style="text-align: right"> 

  [:arrow_up:](#indice)

</div>


## ¿Para qué sirve Markdown? {id='id4'}

Markdown es una forma rápida y fácil de tomar notas, crear contenido para un sitio web y producir documentos listos para imprimir.

- <ins>Sitios web</ins>. Markdown fue diseñado para la web, por lo que no debería sorprender que haya muchas aplicaciones diseñadas específicamente para crear contenido de sitios web.

- <ins>Documentos</ins>. Markdown no tiene todas las comodidades de los procesadores de texto, pero es lo suficientemente bueno para crear documentos como tareas y notas. Puede usar una aplicación de creación de documentos Markdown para crear y exportar documentos con formato Markdown a formato de archivo PDF o HTML. 

- <ins>Notas</ins>. Markdown es la sintaxis ideal para tomar notas. Existen muchas aplicaciones para tomar notas como Obsidian, Simplenote, Notable, Bear, Joplin, Boostnote. 

- <ins>Libros</ins>. ¿Quieres autoeditar una novela? Pruebe Leanpub , un servicio que toma sus archivos con formato Markdown y los convierte en un libro electrónico. Leanpub genera su libro en formato de archivo PDF, EPUB y MOBI. Si desea crear copias de bolsillo de su libro, puede cargar el archivo PDF en otro servicio, como Kindle Direct Publishing.

- <ins>Presentaciones</ins>. Crear presentaciones en Markdown requiere un poco de tiempo para acostumbrarse, pero una vez que aprendes a hacerlo, es mucho más rápido y fácil que usar una aplicación como PowerPoint o Keynote. Remark es una popular herramienta de presentación de diapositivas Markdown basada en navegador, al igual que Cleaver  y Marp.

- <ins>Correo electrónico</ins>. Si envía muchos correos electrónicos y está cansado de los controles de formato disponibles en la mayoría de los sitios web de los proveedores de correo electrónico. Markdown Here es una extensión de navegador gratuita y de código abierto que convierte el texto con formato de Markdown en HTML que está listo para enviar.

- <ins>Colaboración</ins>. Las aplicaciones de colaboración y mensajería en equipo son una forma de comunicarse con compañeros de trabajo y amigos. Estas aplicaciones no utilizan todas las funciones de Markdown, pero las funciones que proporcionan son bastante útiles. Slack, Discord, Wiki.js y Mattermost son buenas aplicaciones de colaboración.

- <ins>Documentación</ins>. Markdown es una opción natural para la documentación técnica. Empresas como GitHub están cambiando cada vez más a Markdown para su documentación.

> Personalmente tomo notas en visual estudio code utilizando el plugin Markdown Preview Enhanced que nos permite previsualizar el documento en vivo.

<div style="text-align: right"> 

  [:arrow_up:](#indice)

</div>


## Sabores de Markdown {id='id5'}

Uno de los aspectos más confusos del uso de Markdown es que prácticamente todas las aplicaciones de Markdown implementan una versión ligeramente diferente de Markdown. Estas variantes de Markdown se conocen comúnmente como sabores. 

Para comprender el concepto de sabores de Markdown, podría ser útil pensar en ellos como dialectos de idiomas.

<div style="text-align: right"> 

  [:arrow_up:](#indice)

</div>

## Sintaxis básica {id='id6'}

- **<ins>Encabezados</ins>**

###### Heading level 6 \######  

##### Heading level 5	\#####  

#### Heading level 4 \####  

### Heading level 3	\###  

## Heading level 2 \##  

# Heading level 1 \#  

- **<ins>Saltos de línea</ins>**. Para crear un salto de línea, termine una línea con \<br> o con dos espacios y luego escriba enter.


- **<ins>Negrita</ins>**. Para agregar texto resaltado en negrita tendrás que usar dos asteriscos ** al principio y al final de lo oración que quieres resaltar.

- **<ins>Cursiva</ins>**. Para agregar texto en cursiva debes usar un solo asterisco * tanto al inicio como al final de lo oración que quieres marcar como cursiva.

- **<ins>Negrita cursiva</ins>**. Para que en texto esté resaltado tanto en negrita como en cursiva al mismo tiempo debes agregar tres asteriscos *** antes y después de una palabra o de una frase. 

- **<ins>Blockquotes</ins>**. Para crear una cita en bloque, agregue un > delante de un párrafo.

> Dorothy followed her through many of the beautiful rooms in her castle.

- <mark>**<ins>Blockquotes con otros elementos</ins>**</mark>. Blockquotes puede contener otros elementos con formato Markdown. No se pueden usar todos los elementos; deberá experimentar para ver cuáles funcionan.

> #### The quarterly results look great!
>
> - Revenue was off the chart.
> - Profits were higher than ever.
>
>  *Everything* is going according to **plan**.


- **<ins>Listas</ins>** En markdown también puedes definir bloques de código, tanto en línea como en forma de bloque. 
<br>

  - Listas ordenadas. Para crear una lista ordenada, agregue elementos de línea con números seguidos de puntos. 

1. First item
2. Second item
3. Third item
4. Fourth item  
<br>

    - Listas desordenadas. Para crear una lista desordenada, agregue guiones (-), asteriscos (*) o signos más (+) delante de las líneas de pedido.

- First item
- Second item
- Third item
- Fourth item  
<br>

- **<ins>Imágenes</ins>** Formato  

  ![Tux, the Linux mascot] (/assets/images/tux.png)  
<br>

- **<ins>Código</ins>** En markdown también puedes definir bloques de código, tanto en línea como en forma de bloque.  
<br>

  - <mark>Código en línea</mark>. Para agregar código en línea en Markdown tendrás que usar comillas invertidas \` alrededor del texto que quieres que tengo formato de código. Ejemplo `cd`.
<br>
  - <mark>Bloques de código</mark>. Para agregar un bloque de código debes utilizar tres comillas invertidas \``` alrededor del texto que quieres que tengo formato de código. También puedes indicar el tipo de código. Ej:

  ```javascript
  let nombre = 'Mauricio'
  console.log(nombre);
  ```
- **<ins>Enlaces</ins>**. Para crear un enlace, encierre el texto del enlace entre corchetes (p. ej., [Duck Duck Go]) y luego sígalo inmediatamente con la URL entre paréntesis (p. ej., (https://duckduckgo.com)).

Para vincular a un elemento en la misma página utilice {id='id1'} en el elemento, y [Texto] (#id1) para referenciarlo.

- **<ins>URL y direcciones de correo electrónico</ins>**. Para convertir rápidamente una URL o una dirección de correo electrónico en un enlace, enciérrelo entre corchetes angulares.

```
<https://www.markdownguide.org>
<fake@example.com>
```

- **<ins>Imágenes</ins>** Para agregar una imagen, agregue un signo de exclamación ( !), seguido del texto alternativo entre paréntesis y la ruta o URL del recurso de imagen entre paréntesis. Opcionalmente, puede agregar un título entre comillas después de la ruta o URL.

![The San Juan Mountains are beautiful!](./assets/images/seagulls-6841129_640.jpg "San Juan Mountains")

<mark>Tamaño de la imagen</mark> La sintaxis de Markdown para imágenes no le permite especificar el ancho y el alto de las imágenes. Si necesita cambiar el tamaño de una imagen puede usar la etiqueta HTML img con los atributos width y height para establecer las dimensiones de una imagen en píxeles.
También puede usar las etiquetas figure y figcaption para agregar un título a su imagen.

<figure>
  <img src="./assets/images/seagulls-6841129_640.jpg" width="300" height="200" target="_blank">
  <figcaption>Gaviotas</figcaption>
</figure>

- **<ins>Símbolos</ins>** Markdown no proporciona una sintaxis especial para los símbolos. Sin embargo, en la mayoría de los casos, puede copiar y pegar cualquier símbolo que desee usar en su documento de Markdown. Por ejemplo, si necesita mostrar Pi (π), simplemente busque el símbolo en una página web y cópielo y péguelo en su documento. 

Alternativamente, si su aplicación Markdown es compatible con HTML , puede usar la entidad HTML para cualquier símbolo que desee usar. Por ejemplo, si desea mostrar el signo de derechos de autor (©), puede copiar y pegar la entidad HTML para derechos de autor (& copy;) en su documento Markdown.


- **<ins>Tablas</ins>**. 

No puede usar muchos elementos de sintaxis de Markdown para dar formato al texto en las celdas de la tabla. Pero existen soluciones para al menos dos problemas comunes de las tablas: saltos de línea y listas.

Saltos de línea dentro de las celdas de la tabla. Puede separar párrafos dentro de una celda de tabla usando una o más \<br> etiquetas HTML.

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title |
| Paragraph   | First paragraph. <br><br> Second paragraph. |

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title |
| List        | Here's a list! <ul><li>Item one.</li><li>Item two.</li></ul> |

- **<ins>Tabla de contenido</ins>** Algunas aplicaciones de Markdown, como Markdeep , pueden generar automáticamente una tabla de contenido (también conocida como toc ) a partir de sus encabezados , pero esta no es una característica proporcionada por todas las aplicaciones de Markdown. Sin embargo, si su aplicación Markdown admite ID de encabezado , puede crear una tabla de contenido para su archivo Markdown usando una lista y algunos enlaces .

##### Table of Contents

- [Underline](#underline)
- [Indent](#indent)
- [Center](#center)
- [Color](#color)
<br>

- **<ins>Video</ins>** Si su aplicación Markdown es compatible con HTML , debería poder incrustar un video en su archivo Markdown copiando y pegando el código HTML proporcionado por un sitio web de videos como YouTube o Vimeo. Si su aplicación Markdown no es compatible con HTML, no puede incrustar un video, pero puede acercarse agregando una imagen y un enlace al video. Podría hacer esto con prácticamente cualquier video en cualquier servicio de video.

Como YouTube lo hace fácil, los usaremos como ejemplo. Tome este video, por ejemplo: https://www.youtube.com/watch?v=8q2IjQOzVpE. La última parte de la URL ( 8q2IjQOzVpE) es la ID del video. Podemos tomar ese ID y ponerlo en la siguiente plantilla:

```
[![Image alt text](https://img.youtube.com/vi/YOUTUBE-ID/0.jpg)](https://www.youtube.com/watch?v=YOUTUBE-ID)
```
YouTube genera automáticamente una imagen para cada video ( https://img.youtube.com/vi/YOUTUBE-ID/0.jpg), por lo que podemos usarla y vincular la imagen al video en YouTube. Después de reemplazar el texto alternativo de la imagen y agregar la ID del video, nuestro ejemplo se ve así:

```
[![Less Than Jake — Scott Farcas Takes It On The Chin](https://img.youtube.com/vi/PYCxct2e0zI/0.jpg)](https://www.youtube.com/watch?v=PYCxct2e0zI)
```
[![Less Than Jake — Scott Farcas Takes It On The Chin](https://img.youtube.com/vi/PYCxct2e0zI/0.jpg)](https://www.youtube.com/watch?v=PYCxct2e0zI)


<div style="text-align: right"> 

  [:arrow_up:](#indice)

</div>
