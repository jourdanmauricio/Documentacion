# Curso de Asincronismo con JavaScript

[https://platzi.com/cursos/asincronismo-js/](https://platzi.com/cursos/asincronismo-js/)
Prof: Oscar Baraja Tavares

## Introducción al asincronismo

El asincronismo es básicamente una manera de aprovechar el tiempo y los recursos de nuestra aplicación, ejecutando tareas y procesos mientras otros son resueltos en background (como la llegada de la información de una API), para posteriormente continuar con las tareas que requerían esa información que no tenías de manera instantánea.

Un ejemplo fácil es comparando asincronismo vs sincronismo: En lenguajes síncronos al hacer un temporizador para ejecutar una función, todo el código se pausa hasta terminar el tiempo, mientras que en Javascript u otros lenguajes asíncronos, podemos estar aprovechando ese tiempo para ejecutar otros procesos hasta que ese tiempo finaliza.

**Event Loop**

• El Event Loop hace que Javascript parezca ser multihilo a pesar de que corre en un solo proceso.

• Javascript se organiza usando las siguientes estructuras de datos:

• Stack. Va apilando de forma organizada las diferentes instrucciones que se llaman. Lleva así un rastro de dónde está el programa, en qué punto de ejecución nos encontramos.

• Memory Heap. De forma desorganizada se guarda información de las variables y del scope.

• Schedule Tasks. Aquí se agregan a la cola, las tareas programadas para su ejecución.

• Task Queue. Aquí se agregan las tares que ya están listas para pasar al stack y ser ejecutadas. El stack debe estar vacío para que esto suceda.

• MicroTask Queue. Aquí se agregan las promesas. Esta Queue es la que tiene mayor prioridad.

• El Event Loop es un loop que está ejecutando todo el tiempo y pasa periódicamente revisando las queues y el stack moviendo tareas entre estas dos estructuras.

Una de las particularidades a considerar al construir apps es no desarrollar funciones muy pesadas, que hagan muchos llamados o procesamientos y que puedan saturar la pila de ejecución, porque no podríamos liberar los callbacks.

## Presentación del reto: consumir APIs

**RESUMEN DEL PROYECTO A REALIZAR:**

1. Consumir la API y obtener cuántos personajes hay en total.
2. Obtener el nombre de cada personaje.
3. Obtener el nombre de la Dimensión a la cual pertenece cada personaje.

Por cada ejercicio consumiremos la API 3 veces. Con callbacks, con promesas y con asyc y awiat.

API: [https://rickandmortyapi.com/](https://rickandmortyapi.com/)

## Definición Estructura Callback

Callback →es una función que al crearla le pasamos como parámetro una segunda función. Y al momento de hacer un llamado asíncrono, la función se ejecuta después del llamado.

**Función Callback.** Una función de **callback** es una función que se pasa a otra función como un argumento, que luego se invoca dentro de la función externa para completar algún tipo de rutina o acción.

```jsx
function date(callback) {
  console.log("1- " + new Date());
  setTimeout(function () {
    let date = new Date();
    callback(date);
  }, 3000);
  console.log("2- Espero");
}

function printDate(dateNow) {
  console.log("3- " + dateNow);
}

date(printDate);
// 1- Fri Apr 15 2022 20:41:01 GMT-0300 (GMT-03:00)
// 2- Espero
// 3- Fri Apr 15 2022 20:41:04 GMT-0300 (GMT-03:00)
```

## Peticiones a APIs usando Callbacks

[https://rickandmortyapi.com/api/character/](https://rickandmortyapi.com/api/character/)

Aclaración de varias cosas que quizás no entiendas si estas empezando:

1. XMLHttpRequest es la forma antigua de hacer llamados, como el profesor lo menciona usa ese y no Fetch que es el actual, por que no conocemos aùn las promesas y fecth es con promesas, para saber por que el profesor uso OPEN y todas esas funciones aqui está la forma de usar XMLHttpRequest : [https://developer.mozilla.org/es/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest](https://developer.mozilla.org/es/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest).
2. " new Error " que el profesor crea, es una nueva instancia de la clase Error que tiene Javascript, son clases ya implicitas que tiene javascript en este caso es para monstrar bien un mensaje de error podemos usarla, más información aqui : [https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Error](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Error).
3. Para los que son fron-end y están aprendiendo de Back, el profesor uso GET por que hace parte de los método http, en este caso necesitamos pedir información a las url ,más información: [https://developer.mozilla.org/es/docs/Web/HTTP/Methods](https://developer.mozilla.org/es/docs/Web/HTTP/Methods)
4. Por ultimo recomiendo una **escucha atenta** a lo que dice el profesor por que el explica el por que de cada cosa que hace y si no la conoces recomiendo buscarlas en Internet y asì avanzas en el curso.

npm install xmlhttprequest —save

```jsx
let XMLHttpRequest = require("xmlhttprequest").XMLHttpRequest;

let API = "https://rickandmortyapi.com/api/character/";

function fetchData(url_api, callback) {
  let xhttp = new XMLHttpRequest();
  // el true es para indicarle que es asíncrona, aunque es el default y podríamos omitirlo
  xhttp.open("GET", url_api, true);
  xhttp.onreadystatechange = function (event) {
    // https://www.w3schools.com/xml/ajax_xmlhttprequest_response.asp
    // Existen 5 estados disponibles:
    // 0. inicializado (aún no se llama a open)
    // 1. cuando se está cargando
    // 2. proceso de carga finalizado
    // 3. Descarga de informacion
    // 4. Completado
    if (xhttp.readyState === 4) {
      if (xhttp.status === 200) {
        // Callback utiliza un estandar en node que indica que:
        // el primer valor que pasamos es el error,
        // y el segundo es la información que se desncadena.
        // En este caso es el resutlado del llamado a la API
        // Tenemos que parsear el resultado a Json porqua la respuesta está en texto
        callback(null, JSON.parse(xhttp.responseText));
      } else {
        console.log(xhttp.status);
        const error = new Error("Error " + url_api);
        return callback(error, null);
      }
    }
  };
  xhttp.send();
}

fetchData(API, function (error1, data1) {
  if (error1) return console.error(error1);

  // Vuelvo a llamar a la API con el id del primer personaje
  fetchData(API + data1.results[0].id, function (error2, data2) {
    if (error2) return console.error(error2);
    // Vuelvo a llamar a la API para traer el origen del personaje
    fetchData(data2.origin.url, function (error3, data3) {
      if (error3) return console.error(error3);

      console.log("Quantity: ", data1.info.count);
      console.log("Name: ", data2.name);
      console.log("Dimension: ", data3.dimension);
    });
  });
});
```

## Implementando Promesas

Para crear una promesa utilizamos la palabra reservada new seguida de la palabra Promise que es el constructor de la promesa. Este constructor recibe un único parámetro que es una función, la cuál a su vez, recibe otros dos parámetros, resolve y reject. El parámetro resolve se utiliza para cuando la promesa devuelve el valor correctamente mientras que reject, se usa en el que caso de que no funcione.

```jsx
const somethingWillHappen2 = () => {
  return new Promise((resolve, reject) => {
    if (false) {
      setTimeout(() => {
        resolve("Hey!");
      }, 2000);
    } else {
      const error = new Error("Whoooops!");
      reject(error);
    }
  });
};
somethingWillHappen2()
  .then((response) => console.log(response))
  .catch((error) => console.error(error));
```

**Promise.all(iterable)**

Devuelve una de dos promesas:

- una que se cumple cuando todas las promesas en el argumento iterable han sido cumplidas,
- o una que se rechaza tan pronto como una de las promesas del argumento iterable es rechazada.

Si la promesa retornada es cumplida, lo hace con un arreglo de los valores de las promesas cumplidas en el mismo orden definido en el iterable.

Si la promesa retornada es rechazada, es rechazada con la razón de la primera promesa rechazada en el iterable. Este método puede ser útil para agregar resultados de múltiples promesas

**Promise.race(iterable)** Devuelve una promesa que se cumple o rechaza tan pronto como una de las promesas del iterable se cumple o rechaza, con el valor o razón de esa promesa.

**Promise.reject(reason)** Devuelve un objeto Promise que es rechazado con la razón dada.

```jsx
const somethingWillHappen = () => {
  return new Promise((resolve, reject) => {
    if (true) {
      resolve("Hey!");
    } else {
      reject("Whoooops!");
    }
  });
};

const somethingWillHappen2 = () => {
  return new Promise((resolve, reject) => {
    if (true) {
      setTimeout(() => {
        resolve("Hey!");
      }, 2000);
    } else {
      const error = new Error("Whoooops!");
      reject(error);
    }
  });
};

Promise.all([somethingWillHappen(), somethingWillHappen2()])
  .then((response) => {
    console.log("Array of results", response);
  })
  .catch((error) => {
    console.error(error);
  });

// Array of results [ 'Hey!', 'Hey!' ]
```

## Conociendo Async/await

Async/await no es mas que **Syntax Sugar**. Es una manera mas *bonita*  de hacer lo mismo que estábamos haciendo con .then(). La clave es recordar que si una función regresa un promesa, podemos usar el keyword **await**, que le indicia al navagador: “Espera a que la promesa se resuelva y almacena su resultado en esta variable”.

Todo esto toma lugar dentro de una función asíncrona, así que usamos **async** para lograr esto.

**Async/await hace que nuestro código se comporte como síncrono.**

```jsx
const doSomethingAsync = () => {
  return new Promise((resolve, reject) => {
    true
      ? setTimeout(() => resolve("Do Something Async"), 3000)
      : reject(new Error("Test error"));
  });
};

const doSomething = async () => {
  const something = await doSomethingAsync();
  console.log(something);
};

console.log("Before");
doSomething();
console.log("After");

const anotherFunction = async () => {
  try {
    const something = await doSomethingAsync();
    console.log(something);
  } catch (error) {
    console.error(error);
  }
};
console.log("Before 1");
anotherFunction();
console.log("After 1");
```

## Callbacks Vs Promesas Vs Async/Await

**Callbacks**

- Ventajas: Simple (una función que recibe otra función). Son universales, corren en cualquier navegador.
- Desventajas: Composición tediosa, anidando cada vez más elementos. Caer en Callback Hell.

**Promesas**

- Ventajas: Facilmente enlazables .Then ( return… ).Then - Fácil e intuitivo de leer
- Desventajas: Posible error si no se retorna el siguiente llamado. No corre en todos los navegadores.

**Async-Await**

- Ventajas: Se puede usar try-catch . Código más ordenado e intuitivo
- Desventajas: No corre en todos los navegadores (se requiere un transpilador).
