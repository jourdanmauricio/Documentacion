# GraphQL

[https://platzi.com/cursos/graphql/](https://platzi.com/cursos/graphql/)

Prof: Adrián Estrada

## Introducción al curso y prerequisitos del curso

Para este curso es necesario tener buenas bases de Node y conocimientos de bases de datos no relacionales como MongoDB. Puedes checar el [Curso Básico de Node.js](https://platzi.com/clases/basico-nodejs/) y el [Curso Básico de MongoDB](https://platzi.com/clases/mongodb/).

## ¿Qué es GraphQL?

**GraphQL** Es un nuevo paradigma a la problemática de tener que comunicar información entre diferentes aplicaciones. Han existido muchas tecnologías que han intentado esto como CORBA, SOPA, RPC, etc. que fueron reemplazadas de forma progresiva hasta llegar a la alternativa más reciente y más usada actualmente, REST.

GraphQL fue creado en el 2015 por Facebook para resolver ciertas limitaciones que se presentaban en REST.

Su principal ventaja es la flexibilidad al momento de requerir información, lo que con REST podría tomar varias consultas y peticiones, en una API de GraphQL bien diseñada solo tomará una única llamada.

GraphQL cuenta con una forma estandarizada para definir todas las interacciones posibles con la información, haciendo posible que la manera de escribir y usar una API sea más predecible y entendible.

### Ventajas

- Un lenguaje agnóstico que permite definir de una forma clara y simple los objetos y acciones del API.
- Una validación automática de la información a ingresar.
- Control de errores de una manera uniforma y predecible.
- Una documentación mínima autogenerada que permite saber exactamente cómo debe ser usado el API tanto a la hora de pedir y enviar información.
- Un entorno de desarrollo amigable donde se pueden probar todas las interacciones.

Especificación →[https://graphql.org/](https://graphql.org/)

## Schema y types

El Schema es la base de una API de GraphQL, consiste en un documento que describe detalladamente los tipos de información que tendrá la API, cada uno especificando qué tipo de campo es.

Los tipos de datos en GraphQL son string, integer, boolean y float.

Para generar un Schema hay que importar la función buildSchema desde graphql y pasarle como parámetro la estructura del esquema. Esta función devuelve un objeto de GraphQL que ya se puede ejecutar.

```jsx
const { graphql, buildSchema } = require("graphql");

// definiendo el esquema
const schema = buildSchema(`
  type Query {
    hello: String
  }
`);

// Ejecutando el query hello
graphql({
  schema: schema,
  source: "{ hello }",
}).then((data) => {
  console.log(data);
});
```

Al ejecutar la función graphql recibe el Schema como primer parámetro y después la propiedad que estamos solicitando, en este caso hello. Devuelve una promesa con la información.

Al ejecutar el script devuelve un objeto data, con la propiedad hello que fue la que se solicitó. Al no haber datos hello es null.

---

El Schema es la base de una API en GraphQL, es el encargado de describir todos los tipos de información que va a contener.

Para la creación de este proyecto usaremos una herramienta llamada `npx`, para ello primero debes instalarlo con el comando:

```bash
npm i -g npx
```

Una vez instalado, dentro de la carpeta de nuestro proyecto vamos a correr el siguiente comando:

```bash
npx license mit > LICENSE && npx gitignore node && git init && npm init -y
```

Ya que termina de correr el comando es momento de añadir la dependencia de GraphQL a nuestro proyecto:

```bash
npm i graphql
```

Dentro de GraphQL contamos con distintos tipos de datos escalares:

- String
- Int
- Float
- Boolean
- ID

> Actualmente tu defines varias APIs tipo REST para traer cierta información. Si quieres añadir nuevos campos al servicio REST que tendrías que hacer? Modificar toda la API para añadir ese campo. GraphQL lo que entraría a hacer es encargarse de llamar esas APIs y tu defines en la query de GraphQL si quieres obtener un campo o quitarlo de tu consulta, así, no tendrías que estar modificando APIs en todo momento si quieres construir una respuesta con unos campos específicos.

> El schema es la estructura de los datos que se pueden consultar y el tipo de dato que es, por ejemplo tu puedes tener una tabla que tiene los post de un blog, esta tabla tiene titulo, fecha de creación, contenido, fecha de actualización, autor del blog, pero tu quieres tener en graphql un schema que solo pueda mostrar el titulo, fecha de actualización y el autor, pero nada más, esto se define en el schema.

## Queries y Resolvers

Una **query** permite ejecutar una petición al API, dentro de una query debes indicar la consulta que quieres ejecutar y los campos que deseas obtener. GraphQL te va a devolver la información que solicitaste dentro del objeto `data`.

El resultado de tu petición no se va a ejecutar de manera mágica, para ello debes definir el objeto `resolvers`, este objeto va a contener una propiedad del mismo nombre que la query que va a resolver o ejecutar.

---

Una Querie permite ejecutar una solicitud hacía la API para traer información. En el Querie se debe indicar la información deseada y qué campos de esa consulta se quiere obtener. Se pueden pedir tantos campos como se desee.

**Resolvers**

Los Resolvers son los que darán la respuesta a las Queries. A partir del ejemplo anterior, para que el hello obtenga una respuesta el resolver debe tener una propiedad hello con un valor.

Para que el Resolver sea tomado en cuenta hay que enviarlo como tercer parámetro a la hora de ejecutar el Query.

## Sirviendo el API en la web

Ya viste que nuestra API funciona a través de la línea de comandos, pero necesitamos que está funcione dentro de la web, para ello necesitas de las dependencias de **express** y un middleware de GraphQL, vamos a instalarlo con el siguiente comando:

```bash
npm i express express-graphql
```

Para evitar el proceso de detener nuestro servidor cada que ejecutamos un nuevo cambio vamos a utilizar la dependencia de desarrollo Nodemon:

```bash
npm i nodemon -D
```

## Custom Types

La belleza del estilo estándar de JavaScript es que es simple. Nadie quiere mantener múltiples archivos de configuración de estilo de cien líneas para cada módulo

Este módulo le ahorra a usted (¡y a otros!) tiempo de tres maneras:

- Sin configuración. La forma más fácil de imponer un estilo coherente en su proyecto. Simplemente colóquelo.
- Formatear automáticamente el código. Simplemente ejecute estándar --fix y diga adiós al código desordenado o inconsistente.
- Detecte los problemas de estilo y los errores del programador con anticipación. Ahorre un valioso tiempo de revisión de código eliminando el ir y venir entre el revisor y el colaborador.

Adoptar un estilo estándar significa clasificar la importancia de la claridad del código y las convenciones de la comunidad por encima del estilo personal. Es posible que esto no tenga sentido para el 100 % de los proyectos y las culturas de desarrollo; sin embargo, el código abierto puede ser un lugar hostil para los novatos. Establecer expectativas claras y automatizadas para los colaboradores hace que un proyecto sea más saludable.

Para obtener más información, consulte la charla de la conferencia "Escribir código perfecto con Standard y ESLint". En esta charla, aprenderá sobre el uso de pelusa, cuándo usar estándar versus eslint y qué tan bonito se compara con el estándar.

Para este proyecto vamos a seguir el estándar de estilos *[Standard](https://standardjs.com/)*, para instalarlo corremos el siguiente comando:

```bash
npm i standard -D
```

GraphQL nos permite configurar nuestros propios tipos de datos, estos deben tener la siguientes sintaxis:

```bash
type <Nombre del tipo> {
  propiedad: Tipo de dato
}
```

Dentro de nuestros tipos de datos podemos configurar un campo de un tipo como obligatorio con el signo “!”, quedando por ejemplo:

```bash
type Course {
  title: String!
}
```

## Argumentos

Vamos a instalar una nueva dependencia para facilitar el trabajo con GraphQL, vamos a correr el siguiente comando:

```bash
npm i graphql-tools
```

Podemos pasar argumentos con distintos tipos de información dentro de las peticiones que hagamos en GraphQL, su sintaxis quedaría de la siguiente manera:

```bash
nombreQuery(campo: tipo): tipo
```

Dentro del resolver los argumentos de la petición pasarían como segundo parámetro, el primero es `root` y el segundo es `args`.

## Configuración de base de datos

Por el momento nuestra API maneja pura información estática, vamos a cambiar esto pasando la información a una base de datos, en este caso usaremos MongoDB.

Es recomendable almacenar las credenciales de conexión a la base de datos como variables de entorno del sistema y utilizar *dotenv* para la lectura de dichas credenciales. Para su instalación vamos a correr el comando

```bash
npm i dotenv
```
