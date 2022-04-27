# Curso Básico de Web Components con JavaScript

[https://platzi.com/cursos/web-components-javascript/](https://platzi.com/cursos/web-components-javascript/)
Prof: Diego De Granda

## ¿Qué problemas resuelven los Web Components?

Los problemas estan relacionados a los distintos ecosistemas o frameworks (React, Angular, Vue), puesto que que estos no pueden coexistir entre sí, por lo que los Web Components al estar fundamentados en JavaScript puro, brinda más compatabilidad.

**Web components** son encapsulados de código, que coexisten entre si

**Problema**

- El desarrollo web se hace más complicado. Actualmente se tiene un ecosistema gigante de JavaScript
  - Varias tecnologías no pueden co existir en un mismo proyecto a la vez, como ser angular con react
  - Debemos elegir bien un stack de tecnologías
- Para solucionar este problema existen Web Components
  - Usan estándares web, para conseguir el mismo resultado e incluso mejor
  - No necesitamos cargar ninguna librería para obtener una arquitectura más escalable

**RESUMEN:** El desarrollo web actualmente se está volviendo complicado debido a que existen muchas tecnologías que si bien facilitan el desarrollo no están dejando usar otras para un mismo proyecto, es ahí donde entran los webs components para obtener el mismo resultado con web api’s

## ¿Qué son los Web Components?

- Los webs components son como piezas de lego. Son partes de código las cuales se pueden reutilizar para obtener un gran resultado. Están creados para ser re utilizables encapsulando código para poder reutilizar en un proyecto o incluso diferentes proyectos **sin necesidad de repetir el código**
- Todos los frameworks dicen tener la filosofía de ser como piezas de lego. Los webs components logran cumplir el objetivo completo, porque se puede implementar web components en cualquier proyecto

> Los web Components son primitivos de bajo nivel que te permiten definir tus propios elementos HMTL

- Te permiten:
  - Generar etiquitas HTML
  - Utilizar estándares Web para construirlos
- Las Web API’s para utilizar web components son
  - **HTML Templates**
  - **Custom Elements** ⇒ Define la etiqueta
  - **Shadow DOM** ⇒ Encapsula el código
  - **ES Modules** ⇒ Módulos para importar y exportar código entre archivos JS

**RESUMEN:** Los web components son fragmentos de código frontend los cuales se pueden usar en cualquier circunstancia sin importar las librerías o frameworks que uses. Para realizar este objetivo están compuestos por una serie de web API’s

## APIs de Web Components

**Custom Elements**

- Es la API que te permite definir la etiqueta usando un web component
- HTML 5 implico una mejora en semántica
  - Brinda nuevas etiquetas como ser `<header> <main> <section <footer>` las cuales mejoran temas como ser:
    - Accesibilidad
    - Marcar secciones el código de una mejor forma
    - Mejorar la lectura del código
  - Actualmente se sigue aumentando el standard
    - Eso implica que si generamos etiquetas propias puede haber un conflicto de nombres
- Para evitar el problema de colisión de nombres se debe nombrar los elementos con dos palabras `my-component`
  - Debido a que el standard sigue la regla que las nuevas etiquetas que se introducen son con solo una palabra

**Shadow DOM**

- No es una alternativa al virtual DOM
- La etiqueta `video` cuenta con Shadow DOM
  - Esta etiqueta cuenta con cosas programadas como ser
    - Botones de play, pausa y agrandar
    - Barras interactivas como ser el avance del video y el volumen del mismo
    - Estilos propios
  - Los estilos nunca tendrán un conflicto con nuestros estilos debido a que está usando el shadow DOM
- Es decir que el código vive dentro del shadow DOM (etiqueta) y no coexiste con el código de afuera resolviendo el problema de conflictos con los estilos

**HTML Template**

- Es una etiqueta de HTML
- No se puede usar directamente con HTML
  - Se debe usar JS para utilizarla
- Regresa un `document fragment`
  - Es un fragmento, parte del document que necesita ser clonado para ser renderizado
- Utilizar esta etiqueta hace que todo el contenido no se muestre
  - Nos da performance, porque no se renderiza directamente

**ES Modules**

- Nos permite re utilizar el código de otros archivos
- HTML Imports
  - Importaba el contenido HTML de otro
  - Pero no fue standard

**RESUMEN:** Para crear web components se necesitan cuatro tecnologías, Custom Elements para crear etiquetas de HTML, Shadow DOM para no tener conflictos con el código externo y pueda vivir nuestro código en diferentes lugares y finalmente ES Modules para poder reutilizar el código

## Beneficios de Web Components

- **Reutilización**
  - Don’t repeat yourself
  - Web Components ⇒ Construyes una sola vez y lo utilizas para siempre
- **Legibilidad**
  - Reduce el código a cosas más simples y directas
- **Mantenibilidad**
  - Cada uno de los componentes pueden ser escritos y probados de forma individual
  - Si un componente se rompe entonces no afectara al resto de la aplicación
- **Interoperabilidad**
  - Los frameworks y librerías no están hechos para coexistir entre ellos
  - Los web components si
- **Consistencia**
  - Los componentes pueden vivir en cualquier framework o librería
  - Puede llegar a ser bastante personalizable

## Ciclo de vida de un componente

El ciclo de vida de un componente están 100% ligados al dom porque son estándares y esto existe en el navegador son parte del [critical renderig path](https://developer.mozilla.org/en-US/docs/Web/Performance/Critical_rendering_path)

**Constructor**

El constructor hace parte de las clases con las que vamos a construir un componente, este es el primer paso del ciclo de vida porque en el critical rendering path junto con el engine de js cuando generamos un constructor estamos guardando en memoria de js que es lo que tiene nuestro constructor y que hace parte también de la clase.

También porque estamos generando una clase que extiende de otra.

**Connected Callback**

Cuando el elemento que seria nuestro componente ya hace parte del dom y aquí es cuando podes realizar cierta actividad importante del componente como empezar a renderizar todo el html y css.

Es mala practica pintar el template directamente, esto es malo ya que en el constructor debemos asegurarnos que todo lo que tiene que estar en memoria exista en ese momento para cuando queramos pintar el elemento en el dom

**Disconected Callback**

El momento en que quitamos un elemento lo estamos desconectando del dom, esto es importante ya que en el momento de eliminar estos elementos pueden tener cierta funcionalidad que también tenemos que desconectar para liberar memoria.

**AttributeChangedCallback**

Es importante porque es la forma en la cual adentro del componente vamos a ver los atributos de nuestra etiqueta html que es nuestro componente que va a tener

Si tenemos ciertos cambios en los atributos este nos lo va a indicar para poder hacer cambios adentro del componente

**AdoptedCallback**

!Es algo que nunca vas a utilizar

Porque es cuando ocupas un componente dentro de un iframe por ejemplo.

Y es mala practica utilizarlo por permance y por mala experiencia para el usuario.

## Custom Elements

AL código

## Template

Es opcional. Pero si adentro de tu componente van a venir muchos elementos que se conviertan en nodos, lo ideal sería ocupar templates.

**Recuerda:** todo lo que esté dentro de la etiqueta `<Template></Template>` NO se va a renderizar de inicio.

Es importante que `cloneNode(true)` tenga el valor de true porque así podrá copiar todos los elementos anidados del HTML.

Podemos meter estilos con JS pero entrarán en conflicto con otros estilos, pero para esto usaremos ShadowDOM.

## Shadow DOM

Con esta implementación podremos solucionar los problemas con los estilos css que se rescriben por temas de especificidad.

Generando como un encapsulado, un dom independiente dentro de nuestro dom global, esto que quiere decir que todo lo que coexista en nuestro dom independiente no va existir dentro de nuestro dom global.

## Content Slot

Es una etiqueta de HTML 5 que nos va a ayudar a poder generar el placeholder en donde irá el texto o cierto contenido que necesitemos para que, afuera de le etiqueta, nosotros podamos pasarle contenido que el componente pueda renderizar.

Básicamente modificamos la etiqueta en HTML y JS hará el trabajo sucio por nosotros.

```jsx
<my-element>Soy texto dentro del slot</my-element>
```

## Multi Content Slot

Si queremos agregar más información necesitamos hacer modificaciones en las diferentes etiquetas que usaremos de slot. Le agregamos el atributo `<slot name="algo"></slot>`. En la etiqueta HTML haremos `<span slot="algo"></span>` . Así vinculamos ambas etiquetas.

```jsx
<my-element>
  <span slot="title">Soy el h2 que está en el slot de JS</span>
  <span slot="paragraph">Soy el p que está en el slot de JS</span>
</my-element>
```

---

## Atributos

Crearemos nuestros propios atributos en JS para colocarlos en la etiqueta HTML. Así mandamos información de manera sencilla.

```jsx
<my-element
  title="Soy un título :D"
  parrafo="Soy el texto del párrafo"
  img="https://avatars3.githubusercontent.com/u/1905708?s=280&v=4"
></my-element>
```

## attributeChangedCallback

La manera que usamos atributos en el tema anterior, funciona. Pero lo correcto es hacer uso del ciclo de vida llamado: **attributeChangedCallback**

ya que así nos aseguramos de tener un componente completamente dinámico capaz de cambiar sus valores de acuerdo a las necesidades del desarrollador.

En resumen, esto lo logramos añadiendo un

```
static get observedAttributes()
```

, que señala cuáles son los atributos que se van a estar observando sus cambios mediante un return de un array, y añadiendo el ciclo de vida attributeChangedCallback(), que es donde vamos a definir los nuevos valores a renderizar.

## disconnectedCallback

[https://developer.mozilla.org/es/docs/Web/Web_Components/Using_custom_elements#usando_callbacks_de_ciclo_de_vida](https://developer.mozilla.org/es/docs/Web/Web_Components/Using_custom_elements#usando_callbacks_de_ciclo_de_vida)

disconnected callback nos servirá para deslindar de eventos a nuestros componente, dentro de esa función podremos retirarlos para liberar espacio en memoria.

## host

En estas clases veremos los estilos que se manejaran tanto fuera como dentro de los web components

:host es una pseudoclase para darle estilo que define a nuestro componente web que no quiere decir que son necesariamente visuales, si no que son los estilos que ya vienen previamente definidos en la pseudeclase `host`  de ese elemento.

Nosotros podemos definir esos estilos base que nos ayudan a definir ciertas características base para poder modificar los estilos de nuestra manera.

La pseudoclase :host se utiliza dentro del método donde escribíamos nuestro css del componente getStyles(){} y tiene que estar dentro de las etiquetas style para que funcionen estos estilos.

Nosotros podemos definir esos estilos base que nos ayudan a definir ciertas características base para poder modificar los estilos de nuestra manera.

La pseudoclase :host se utiliza dentro del método donde escribíamos nuestro css del componente getStyles(){} y tiene que estar dentro de las etiquetas style para que funcionen estos estilos.

```jsx
<style>
      :host{

        display: inline-block;
        with:100%;
        min-width: 300px;
        max-width: 450px;
        font-size:20px;
        background: grey;
      }
</style>
```

utilizando esta pseudo clase podremos añadirle estilos base a nuestro elemento host le dará estilos al componente y los que estén fuera del :host son los que le darán estilo a los elementos que están dentro de nuestro componente.

Aqui le decimos al pseudclase host que si encuentra un elemento con la clase blue haga lo siguiente

En este caso solo cambiaria al componente que tenga la clase blue

A los demás si le agrega los cambios que ya tenían previamente.

```jsx
getStyles(){
    return`
    <style>
      :host{

        display: inline-block;
        with:100%;
        min-width: 300px;
        max-width: 450px;
        font-size:20px;
        background: grey;
      }


      :host(.blue){
        background:blue;
      }
      </style>
    `
  }
```

También podemos darle estilos por atributos, entonces lo que hacemos es indicarle un atributo a nuetro elemento

:**host([atributo]){}**

Tambien podremos agregar estilos por contexto, es decir le indicamos a nuestra pseudoclase el elemento donde esta nuestro componente junto con su clase y podremos agregarle estilos

:**host-context([padreDeNuestroComponente]){}**

```jsx
:host-context(article.card){
        display:block;
        max-width: 100%;
      }
      </style>
```

Cambiando estilos al contenido del componente

```jsx
:host([yellow]) h2{
        color: grey;
      }
      :host([yellow]) p{
        color: red;
      }
```

## ::slotted

En esta clase utilizaremos el pseudoelemento sloted que nos ayudara a agregarle estilos especificos a todo el contenido dinámico que venga fuera del componente y se vaya a agregar en todas las etiquetas slot que estan fuera de nuestro componente.

Este elemento solo se va a poder trabajar una vez estemos utilizando el shadow dom

Podremos usar la pseudo clase sloted con el selector \* para seleccionar todas las etiquetas que estan por fuera.

```jsx
::slotted(*){

        }
        ::slotted(span){
          font-size:30px;
          color:red;
        }
```

También podremos seleccionar exactamente a cual etiqueta esta por fuera agregarle estilos

::**sloted**(**etiquetaFuera**){estilos}

```jsx
::slotted(span){
          font-size:30px;
          color:red;
}
```

También podremos cambiar los estilos utilizando una clase que tenga la etiqueta

```jsx
::slotted(.text){
    color:blue;
}
```

## CSS custom properties

Como se ha comentado en anteriores clases generar un componente reutilizable implica que no tenemos que ir hasta el código de este y cambiarlo, entonces lo que haremos es re asignar nuestros estilos por fuera.

Con shadow dom esta idea que se plantea de poder cambiar nuestros estilos por fuera no es posible, pero esto en cierto punto es mentira ya que podremos hacerlo atraves de las Custom Properties que son unas variables en donde las generamos y de valor estas tienen un estilo.

Lo que haremos es definir variables en nuestros host y luego agregárselas a nuestros elementos que estan dentro de los componentes para probarlas.

```jsx
:host{
          --primary-color:tomato;
          --secundary-color:salmon;
          --heading-primary: 30px;
          --heading-secundary: 25px;
          display: inline-block;
          width:100%;
          min-width:300px;
          max-width: 450px;
        }
        section{
          background:var(--primary-color);
        }
        section div{
          background: var(--secundary-color);
        }
        h1{
          font-size: var(--heading-primary)
        }
        p{
          font-size: var(--heading-secondary)
        }
```

Luego para poderlas modificar desde fuera del codigo establecido en el componente, lo que hacemos es modificarlas desde nuestro css, seleccionando lo que queremos modificar y reasignando el valor de la variable.

```jsx
my-element{
      --primary-color:blue;
      --heading-primary:40px;
    }
    .segundo{
      --primary-color:red;
    }
    .tercero{
    --secundary-color: lime;
    }
```

Podremos utilizar como selector el componente y clases que le establezcamos al componente.
