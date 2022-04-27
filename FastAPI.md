# FastAPI: Fundamentos, Path Operations y Validaciones

https://platzi.com/cursos/fastapi/
prof: Facundo García Martoni

## ¿Qué es FastAPI?

<font color="green">FastAPI</font>, es el framework más veloz para el desarrollo web con Python, particularmente backend, APIS. Es un o de los frameworks más rápidos, compite con GO.

Creado por Sebastián Ramirez (@tiangolo). Es open source.

## Ubicación de FastAPI en el ecosistema de Python

<u>FastAPI utiliza otros frameworks dentro de si para funcionar</u>

- **Uvicorn**: es una librería de Python que funciona de servidor, es decir, permite que cualquier computadora se convierta en un servidor

- **Starlette**: es un framework de desarrollo web de bajo nivel, para desarrollar aplicaciones con este requieres un amplio conocimiento de Python, entonces FastAPI se encarga de añadirle funcionalidades por encima para que se pueda usar mas fácilmente

- **Pydantic**: Es un framework que permite trabajar con datos similar a pandas, pero este te permite usar modelos los cuales aprovechara FastAPI para crear la API

FastAPI es un framework que está parado sobre los hombros de gigantes, esos gigantes son Uvicorn, Starlette y Pydantic.

## Hello World: creación del entorno de desarrollo

1. Crear carpeta llamada fast-api-hello-word

`cd fast-api-hello-word`

2. Crear entorno virtual

`py -m venv venv`

3. activar entorno virtual

`source venv/bin/activate`

4. Instalamos fastapi y el servidor uvicorn

`pip install fastapi uvicorn`

5. `Code .` Creamos un archivo llamado `main.py`

6. `git init`

7. Crear el archivo `.gitignore` y agregar:

`venv/`

8. `git add .` y `git commit -m "First commit"`

## Hello World: elaborando el código de nuestra primer API

```python
# main.py
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def home():
    return {"Hellow": "word"}
```

Levantamos el servidor desde la terminal:

```bash
$uvicorn main:app --reload
```

## Documentación interactiva de una API

FastAPI documenta el código correctamente. Está parado sobre los hombros de <font color="violet">OpenAPI (es una especificación), el cual es un conjunto de reglas que permite definir cómo describir, crear y visualizar APIs. Es un conjunto de reglas que permiten decir que una API está bien definida</font>

OpenAPI necesita de un software, el cual es Swagger, que es un conjunto de softwares que permiten trabajar con APIs. FastAPI funciona sobre un programa de Swagger el cual es Swagger UI, que permite mostrar la API documentada en html

- Acceder a la documentación interactiva con Swagger UI: localhost/docs
- Acceder a la documentación interactiva con Redoc: localhost/redoc

## Path Operations

<u>¿Que es un path (route, endpoint)?</u> Un path es lo mismo que un route o endpoints y es todo aquello que vaya después de nuestro dominio a la derecha del mismo.

<u>¿Que son las operations?</u> Un operations es exactamente lo mismo que un método http y tenemos las siguientes más populares: GET, POST, PUT, DELETE, OPTIONS, HEAD, PATCH …

- GET solicita una representación del recurso especificado. Las solicitudes que utilizan GET solo deben recuperar datos.
- HEAD solicita una respuesta idéntica a GET, pero sin el cuerpo de la respuesta.
- POST envía una entidad al recurso especificado, lo que a menudo provoca un cambio de estado o efectos secundarios en el servidor.
- PUT reemplaza todas las representaciones actuales del recurso de destino con la carga útil de la solicitud.
- DELETE elimina el recurso especificado.
- CONNECT establece un túnel al servidor identificado por el recurso de destino.
- OPTIONS describe las opciones de comunicación para el recurso de destino.
- TRACE realiza una prueba de bucle de mensajes a lo largo de la ruta al recurso de destino.
- PATCH aplica modificaciones parciales a un recurso.

## Path Parameters

<u>Path Parameters</u> Podemos crear variables dentro de los endpoints, se les llama Path Parameters. Si yo los defino, entonces es obligatorio usarlos.

Por ejemplo: /tweets/{tweet_id}

## Query Parameters

<u>Query Parameters</u>: es un conjunto de elementos opcionales los cuales son añadidos al finalizar la ruta, con el objetivo de definir contenido o acciones en la url, estos elementos se añaden despues de un ?
para agregar más query parameters utilizamos &

Ej: `PUT /users/{user_id}/details?age=20&heiht=184`

## Request Body y Response Body

<u>Request Body y Response Body</u>

Debes saber que bajo el protocolo HTTP existe una comunicación entre el usuario y el servidor. Esta comunicación está compuesta por cabeceras (headers) y un cuerpo (body).

Se tienen dos direcciones en la comunicación entre el cliente y el servidor y definen de la siguiente manera:

- Request : Cuando el cliente solicita/pide datos al servidor.
- Response : Cuando el servidor responde al cliente.
- Request Body: es el cuerpo (body) de una solicitud del cliente al servidor.
- Response Body: es el cuerpo (body) de una respuesta del servidor al cliente.

---

En nuestro proyecto creamos una rama:

```bash
$git checkout -b "request_response_body"
$git branch
```

Luego creamos una ruta:

```python
@app.post("/person/new")
def create_person():
    ...
```

## Models

- Entidad: es cualquier objeto que nos rodea
- Modelo: es la representación de una entidad en código, al menos de manera descriptiva, por lo que cada entidad debe tener por lo menos un modelo. Esto se logra con una librería llamada pydantic, de ella traeremos una clase llamada BaseModel para crear los modelos.

<u>Cómo creamos los modelos</u>:

```python
# Haremos tipado estático
from typing import Optional

from pydantic import Base model

from fastapi import Body

class Person(BaseModel):
    first_name: str
    last_name: str
    age: int
    hair_Color: Optional[str] = None
    is_married: Optional[bool] = None

@.app.post("/person/new")
def_create_person(person: Person = Body(...)):
    return person

# Body Lo utilizamos para indicar qque el parámetro Person es de tipo body.
# Además el ... indica que es obligatorio
```

## Validaciones: Query Parameters

<u>Validaciones</u> Las validaciones tal como se definen, nos sirven para comprobar si son correctos los parámetros entregados en cada una de las peticiones. Estas validaciones funcionan restringiendo o indicando el formato de entrega en cada una de las peticiones.

<u>Query parameters</u> Entonces, se definen las validaciones para las Query Parameters para definir un estándar de consulta y especificar cómo se deben entregar los datos.

Ej: Se define la siguiente consulta (QUERY):

`https://domain.com/user/detail?nombre=Manolo&edad=20`

Como validaciones tendríamos que limitar el tamaño de caracteres que puede tener el atributo “nombre” (50 > largo > 1), además de limitar los valores para “edad” (300 > edad > 0).

```python
from fastapi import Body, Query
# Validaciones: query parameters.

@mi_app.get("/user/detail") # Ruta para realizar la consulta.
def show_user(# opcional (parametros=default, longitud mínima, longitud máxima)
    nombre: Optional[str] = Query(None, min_length=1, max_length=50),
	# Obligatorio.
	edad: int = Query(...)
   ):

   return {nombre: edad};
```

## Validaciones: explorando más parameters

Para especificar las validaciones, debemos pasarle como parámetros a la función Query lo que necesitemos validar.

<u>Para tipos de datos str</u>:

- max_length : Para especificar el tamaño máximo de la cadena
- min_length : Para especificar el tamaño minimo de la cadena
- regex : Para especificar expresiones regulares

<u>Para tipos de datos int</u>:

- ge : (greater or equal than ≥) Para especificar que el valor debe ser mayor o igual
- le : (less or equal than ≤) Para especificar que el valor debe ser menor o igual
- gt : (greater than >) Para especificar que el valor debe ser mayor
- lt : (less than <) Para especificar que el valor debe ser menor

Ej:

```python
# Validaciones de un nombre de usuario.
Query(None, min_length=1, max_length=50)):
```

Validar un email:

.+ = Obliga a contener uno o mas caracteres  
@ = Obliga a tener un @  
. = Obliga a tener un .

```python
email: str = Query(..., regex=".+@.+\..+")
```

Es posible dotar de mayor contexto a nuestra documentación. Se deben usar los parámetros title y description.

- title : Para definir un título al parámetro.
- description : Para especificar una descripción al parámetro.

```python
# Validaciones para un Identificador.
Query(
	None,
	title="ID del usuario",
	description="El ID se consigue entrando a las configuraciones del perfil");
```

## Validaciones: Path Parameters

También podemos aplicar validaciones sobre los path parameters.

Ejemplo:

```python
from fastapi import Body, Query, Path

# Validaciones: Query Parameters

@app.get("/person/detail")
def show_person(
    name: Optional[str] = Query(
        None,
        min_length=1,
        max_length=50,
        title="Person Name",
        description="This is the person name. It's between 1 and 50 characters"
        ),
    age: str = Query(
        ...,
        title="Person Age",
        description="This is the person age. It's required"
        )
):
    return {name: age}

# Validaciones: Path Parameters

@app.get("/person/detail/{person_id}")
def show_person(
    person_id: int = Path(..., gt=0)
):
    return {person_id: "It exists!"}
```

## Validaciones: Request Body

Finalmente podemos validar los parámetros que lleguen en el body del request.

```python
# Validaciones: Request Body
# Models

class Location(BaseModel):
    city: str
    state: str
    country: str

class Person(BaseModel):
    first_name: str
    last_name: str
    age: int
    hair_color: Optional[str] = None
    is_married: Optional[bool] = None

# Routes

@app.put("/person/{person_id}")
def update_person(
    person_id: int = Path(
        ...,
        title="Person ID",
        description="This is the person ID",
        gt=0
    ),
    person: Person = Body(...),
    location: Location = Body(...)
):
    results = person.dict()
    results.update(location.dict())
    return results
```

- dict -> de json a diccionario
- update -> combina diccionarios

> Si necesitamos recibir 2 jsons como input se especifican separadod en la declaración del path pero FastApI lo organiza de la siguiente manera:

```json
body: {
  "person": {
    ...
  },
  "location": {
    ...
  }
}
```

## Validaciones: Models

Podemos validar los atributos que se encuentran dentro del request body. Se realiza dentro del modelo.

Agregamos validaciones a los modelos que teníamos.

> Nota: ver el modelo hair_color. Al inicio del modelo crea un enum con los colores posibles. Luego, en la definición del atributo colocamos que es del tipo enum creado.

```python
#Python
from typing import Optional
from enum import Enum
#Pydantic
from pydantic import BaseModel
from pydantic import Field
#FastAPI
from fastapi import FastAPI
from fastapi import Body, Query, Path

app = FastAPI()
# Models

class HairColor(Enum):
    white = "white"
    brown = "brown"
    black = "black"
    blonde = "blonde"
    red = "red"

class Location(BaseModel):
    city: str
    state: str
    country: str

class Person(BaseModel):
    first_name: str = Field(
        ...,
        min_length=1,
        max_length=50,
        example="Miguel"
        )
    last_name: str = Field(
        ...,
        min_length=1,
        max_length=50,
        example="Torres"
        )
    age: int = Field(
        ...,
        gt=0,
        le=115,
        example=25
    )
    hair_color: Optional[HairColor] = Field(default=None, example=HairColor.black)
    is_married: Optional[bool] = Field(default=None, example=False)
```

## Tipos de datos especiales

Todos estos tipos de datos corresponden a Pydantic, se pueden importar al igual que Field.

<u>Tipos de datos clásicos</u>:

- str → Cadena de texto
- int → Número entero
- float → Número flotante (decimal)
- bool → Booleano

<u>Tipos de datos exóticos</u>:

- Enum → Enumerar caracteres
- HttpUrl → Revisa si una URL es valida (https://myapp.com, www.google.com)
- FilePath → Valida si la ruta que envía el cliente es un archivo (c:/windows/system32/432.dll)
- DirectoryPath → Valida si la ruta que envía el cliente es un directorio (/mnt/c/someFolder)
- EmailStr → Valida si el cliente ingresa un email (hola@email.com)
- PaymentCardNumber → Valida si el cliente ingresa un número de tarjeta
- IPvAnyAdress → Valida si el cliente ingresa una dirección IP
- NegativeFloat → Valida si el cliente ingresa un número negativo de tipo flotante
- PositiveFloat → Valida si el cliente ingresa un número positivo de tipo flotante
- NegativeInt → Valida si el cliente ingresa un número entero negativo
- PositiveInt → Valida si el cliente ingresa un número entero positivo

Para más tipos de datos se puede revisar la documentación de Pydantic. https://pydantic-docs.helpmanual.io/usage/types/#pydantic-types

## Creando ejemplos de Request Body automáticos

El sistema de autodocumentación de Swagger (localhost/docs) nos permite probar cada endpoint. Es bastante psado tener que "llenar" un json con cada ejecución, por que FastAPI nos permite incorporar una subclase dentro de cada modelo para que se autocomplete la documentación de manera de no tener que ingresar todos los datos al JSON.

```python
class Person(BaseModel):
    first_name: str = Field(
        ...,
        min_length=1,
        max_length=50,
        example="Miguel"
        )
    last_name: str = Field(
        ...,
        min_length=1,
        max_length=50,
        example="Torres"
        )
    age: int = Field(
        ...,
        gt=0,
        le=115,
        example=25
    )
    hair_color: Optional[HairColor] = Field(default=None, example=HairColor.black)
    is_married: Optional[bool] = Field(default=None, example=False)

    #class Config:
    #    schema_extra = {
    #        "example": {
    #            "first_name": "Facundo",
    #            "last_name": "García Martoni",
    #            "age": 21,
    #            "hair_color": "blonde",
    #            "is_married": False
    #        }
    #    }
```

Otra forma es no utilizar esta clase particular. Debemos incorporar la llave example en la definición del campo. En el ejemplo, en el campo name coloco "Facundo" y en last_name = "Torres", age=25....

## Creando ejemplos de Path y Query parameters automáticos

También podemos crear ejemplos para las rutas y parámetros. Se utiliza la sintaxis example en la definición del path

<u>Validaciones: Query Parameters</u>

```python
@app.get("/person/detail")
def show_person(
    name: Optional[str] = Query(
        None,
        min_length=1,
        max_length=50,
        title="Person Name",
        description="This is the person name. It's between 1 and 50 characters",
        example="Rocío"
        ),
    age: str = Query(
        ...,
        title="Person Age",
        description="This is the person age. It's required",
        example=25
        )
):
    return {name: age}

# Validaciones: Path Parameters

@app.get("/person/detail/{person_id}")
def show_person(
    person_id: int = Path(
        ...,
        gt=0,
        example=123
        )
):
    return {person_id: "It exists!"}
```
