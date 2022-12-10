<div align='center'>
<img height="60" src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/a7/React-icon.svg/539px-React-icon.svg.png">
<h2>Preguntas de entrevista técnica React</h2>

_De cero a experto. Las preguntas estan divididas en tre secciones. `Principiante`, `Intermedio` y `Experto`._

_Para llegar a ellas deberas ir desplegando cada una de las secciones hasta la pregunta y abajo en forma contraida encontrarás las respuestas detalladas en Español_
</div>
<div align='right'>
<sup>Deja tu ⭐ si te gusta el proyecto.</sup>
</div>

---
<h2>Principiante</h2>
<details><summary><i>👉  &nbsp&nbsp Comenzar</i></summary>

---
<p>
<ol start= '1'>
<li>
<details><summary><i>Requisitos para dominar React</i></summary>
<p>
<ol start= '1'>
<li>
<details><summary><i>¿JavaScript que necesitas para aprender React?</i></summary>
<p>

**Para aprender y dominar React necesitas saber JavaScript.** A diferencia de otros frameworks y bibliotecas, como *Angular* y *Vue*, que se basan en su propio *DSL* (Domain-Specific Language), React usa una extensión de la sintaxis de JavaScript llamada *JSX*. Más adelante lo veremos en detalle pero, al final, no deja de ser azúcar sintáctico para escribir menos JavaScript.

**En React todo es JavaScript.** Para bien y para mal. Este libro da por sentados unos conocimientos previos del lenguaje de programación pero antes de empezar vamos a hacer un pequeño repaso por algunas de las características más importantes que necesitarás conocer.

**Si ya dominas JavaScript puedes saltarte este capítulo** y continuar con el libro, pero recuerda que siempre podrás revisar este capítulo como referencia.

##### EcmaScript Modules o ESModules

Los **EcmaScript Modules** es la forma nativa que tiene JavaScript para importar y exportar variables, funciones y clases entre diferentes ficheros. Hoy en día, especialmente si trabajamos con un empaquetador de aplicaciones como Webpack, vamos a estar trabajando constantemente con esta sintaxis.

Por un lado podemos crear módulos exportándolos por defecto:

```js
// sayHi.js
// exportamos por defecto el módulo sayHi
export default sayHi (message) {
    console.log(message)
}

// index.js
// este módulo lo podremos importar con el nombre que queramos
import sayHi from './sayHi.js'

// al ser el módulo exportado por defecto podríamos usar otro nombre
import miduHi from './sayHi.js'
```

También podemos hacer exportaciones nombradas de módulos, de forma que un módulo tiene un nombre asignado y para importarlo necesitamos usar exactamente el nombre usado al exportarlo:

```js
// sayHi.js
// podemos usar exportaciones nombradas para mejorar esto
export const sayHi = (message) => console.log(message)

// y se pueden hacer tantas exportaciones de módulos nombrados como queramos
export const anotherHi = msg => alert(msg)

// index.js
// ahora para importar estos módulos en otro archivo podríamos hacerlo así
import {sayHi, anotherHi} from './sayHi.js'
```

Los *imports* que hemos visto hasta aquí se conocen como *imports estáticos*. Esto significa que ese módulo será cargado en el momento de la carga del archivo que lo importa.

También existen los *imports dinámicos*, de forma que podamos importar módulos que se carguen en el momento de la ejecución del programa o cuando nosotros decidamos (por ejemplo, como respuesta a un click).

```js
document.querySelector('button').addEventListener('click', () => {
  // los imports dinámicos devuelven una Promesa
  import('./sayHi.js').then(module => {
    // ahora podemos ejecutar el módulo que hemos cargado
    module.default('Hola')
  })
})
```

A> Los imports dinámicos son útiles también cuando trabajamos con empaquetadores como Webpack o Vite, ya que esto creará unos *chunks* (fragmentos) que se cargarán fuera del bundle general. ¿El objetivo? Mejorar el rendimiento de la aplicación.

Existen más sintaxis para trabajar con módulos, pero con saber las que hemos visto ya sería suficiente para seguir el libro.

**¿Por qué es importante**

Para empezar React te ofrece diferentes partes de su biblioteca a través de módulos que podrás importar. Además nuestros componentes los tendremos separados en ficheros y, cada uno de ellos, se podrá importar utilizando *ESModules*.

Además, por temas de optimización de rendimiento, podremos importar de forma dinámica componentes y así mejorar la experiencia de nuestros usuarios al necesitar cargar menos información para poder utilizar la página.

</p>
</details>
</li>
<li>
<details><summary><i>Operador condicional (ternario)</i></summary>
<p>

Las ternarias son una forma de realizar condiciones sin la necesidad de usar la sintaxis con `if`. Se podría decir que es una forma de atajo para evitar escribir tanto código.

```js
if (number % 2 === 0) {
  console.log('Es par')
} else {
  console.log('Es impar')
}

// usando ternaria
number % 2 === 0 ? console.log('Es par') : console.log('Es impar')
```

**¿Por qué es importante**

En las interfaces gráficas es muy normal que, dependiendo del estado de la aplicación o los datos que nos lleguen, vamos a querer renderizar una cosa u otra en pantalla. Para realizar esto, en lugar de utilizar `if` se usan las ternarias ya que queda mucho más legible dentro del *JSX*.

</p>
</details>
</li>
<li>
<details><summary><i>Funciones flecha o Arrow Functions</i></summary>
<p>

Las *funciones flecha* o *arrow function* fueron añadidas a JavaScript en el estándar ECMAScript 6 (o ES2015). En principio parece que simplemente se trata de una sintaxis alternativa más simple a la hora de crear expresiones de funciones:

```js
const nombreDeLaFuncion = function (param1, param2) {
  // instrucciones de la función
}

const nombreDeLaFuncion = (param1, param2) => { // con arrow function
  // instrucciones de la función
}
```

Pero además del cambio de sintaxis existen otras características de las funciones flechas que se usan constantemente en React.

```js
// return implícito al escribir una sola línea
const getName = () => 'midudev'

// ahorro de parentésis para función de un parámetro
const duplicateNumber = num => num * 2

// se usan mucho como callback en funciones de arrays
const numbers = [2, 4, 6]
const newNumbers = numbers.map(n => n / 2)
console.log(newNumbers) // [1, 2, 3]
```

También tiene algunos cambios respecto al valor de `this` pero, aunque es aconsejable dominarlo, no es realmente necesario para poder seguir con garantías el libro.

**¿Por qué es importante**

Aunque hace unos años con React se trabajaba principalmente con clases, desde la irrupción de los hooks en la versión 16.8 ya no se usan mucho. Esto hace que se usen mucho más funciones.

Las funciones flecha, además, puedes verlas fácilmente conviviendo dentro de tus componentes. Por ejemplo, a la hora de renderizar una lista de elementos ejecutarás el método `.map` del array y, como callback, seguramente usarás una función flecha anónima.
</p>
</details>
</li>
<li>
<details><summary><i>Parámetros predeterminados (default values)</i></summary>
<p>

En JavaScript puedes proporcionar valores por defecto a los parámetros de una función en caso que no se le pase ningún argumento.

```js
// al parámetro b le damos un valor por defecto de 1
function multiply(a, b = 1) {
  return a * b;
}

// si le pasamos un argumento con valor, se ignora el valor por defecto
console.log(multiply(5, 2)) // 10

// si no le pasamos un argumento, se usa el valor por defecto
console.log(multiply(5)) // 5

// las funciones flecha también pueden usarlos
const sayHi = (msg = 'Hola React!') => console.log(msg)
sayHi() // 'Hola React!'
```

**¿Por qué es importante**

En React existen dos conceptos muy importantes: **componentes y hooks**. No vamos a entrar en detalle ahora en ellos pero lo importante es que ambos son construidos con funciones.

Poder añadir valores por defecto a los parámetros de esas funciones en el caso que no venga ningún argumento **es clave** para poder controlar React con éxito.

Los componentes, por ejemplo, pueden no recibir parámetros y, pese a ello, seguramente vas a querer que tengan algún comportamiento por defecto. Lo podrás conseguir de esta forma.

</p>
</details>
</li>
<li>
<details><summary><i>Template Literals</i></summary>
<p>

Los template literals o plantillas de cadenas llevan las cadenas de texto al siguiente nivel permitiendo expresiones incrustadas en ellas.

```js
const inicio = 'Hola'
const final = 'React'

// usando una concatenación normal sería
const mensaje = inicio + " " + final

// con los template literals podemos evaluar expresiones
const mensaje = `${inicio} ${final}`
```

Como ves, para poder usar los template literals, necesitas usar el símbolo ```

Además, también nos permiten utilizar cadenas de texto de más de una línea.

**¿Por qué es importante**

En React esto se puede utilizar para diferentes cosas. No sólo es normal crear cadenas de texto para mostrar en la interfaz... también puede ser útil para crear clases para tus elementos HTML de forma dinámica. Verás que los template literales están en todas partes.

</p>
</details>
</li>
<li>
<details><summary><i>Propiedades abreviadas</i></summary>
<p>

Desde *ECMAScript 2015* se puede iniciar un objeto utilizado nombre de propiedades abreviadas. Esto es que si quieres utilizar como valor una variable que tiene el mismo nombre que la key, entonces puedes indicar la inicialización una vez:

```js
const name = 'Miguel'
const age = 36
const book = 'React'

// antes haríamos esto
const persona = { name: name, age: age, book: book }

// ahora podemos hacer esto, sin repetir
const persona = { name, age, book }
```

**¿Por qué es importante**

En React se trata muchas veces con objetos y siempre vamos a querer escribir el menor número de líneas posible para mantener nuestro código fácil de mantener y entender.

</p>
</details>
</li>
<li>
<details><summary><i>La desestructuración</i></summary>
<p>

La sintaxis de *desestructuración* es una expresión de JavaScript que permite extraer valores de Arrays o propiedades de objetos en distintas variables.

```js
// antes
const array = [1, 2, 3]
const primerNumero = array[0]
const segundoNumero = array[1]

// ahora
const [primerNumero, segundoNumero] = array

// antes con objetos
const persona = { name: 'Miguel', age: 36, book: 'React' }
const name = persona.name
const age = persona.age

// ahora con objetos
const {age, name} = persona

// también podemos añadir valores por defecto
const {books = 2} = persona
console.log(persona.books) // -> 2

// también funciona en funciones
const getName = ({name}) => `El nombre es ${name}`
getName(persona)
```

**¿Por qué es importante**

En React hay mucho código básico que da por sentado que conoces y dominas esta sintaxis. Piensa que los objetos y los arreglos son tipos de datos que son perfectos para guardar datos a representar en una interfaz. Así que poder tratarlos fácilmente te va a hacer la vida mucho más fácil.

</p>
</details>
</li>
<li>
<details><summary><i>Métodos de Array</i></summary>
<p>
Saber manipular arreglos en JavaScript es básico para considerar que se domina. Cada método realiza una operación en concreto y devuelve diferentes tipos de datos. Todos los métodos que veremos reciben un callback (función) que se ejecutará para cada uno de los elementos del array.

Vamos a revisar algunos de los métodos más usados:

```js
// tenemos este array con diferentes elementos
const networks = [
  {
    id: 'google',
    url: 'http://www,google.com.ar',
    needsUpdate: true
  },
  {
    id: 'twitter',
    url: 'https://twitter.com',
    needsUpdate: true
  },
  {
    id: 'instagram',
    url: 'https://instagram.com',
    needsUpdate: false
  }
]

// con .map podemos transformar cada elemento
// y devolver un nuevo array
networks.map(singleNetwork => singleNetwork.url)
// Resultado:
  [
    'http://www,google.com.ar',
    'https://twitter.com',
    'https://instagram.com'
  ]

// con .filter podemos filtrar elementos de un array que no
// pasen una condición determinada por la función que se le pasa.
// Devuelve un nuevo array.
networks.filter(singleNetwork => singleNetwork.needsUpdate === true)
// Resultado:
[
  { id: 'google', url: 'http://www,google.com.ar', needsUpdate: true },
  { id: 'twitter', url: 'https://twitter.com', needsUpdate: true }
]

// con .find podemos buscar un elemento de un array que
// cumpla la condición definida en el callback
networks.find(singleNetwork => singleNetwork.id === 'google')
// Resultado:
{ id: 'google', url: 'http://www,google.com.ar', needsUpdate: true }

// con .some podemos revisar si algún elemento del array cumple una condición
networks.some(singleNetwork => singleNetwork.id === 'tiktok') // false
networks.some(singleNetwork => singleNetwork.id === 'instagram') // true
```

**¿Por qué es importante**

En React es muy normal almacenar los datos que tenemos que representar en la UI como array. Esto hace que muchas veces necesitemos tratarlos, filtrarlos o extraer información de ellos. Es primordial entender, conocer y dominar al menos estos métodos, ya que son los más usados.

</p>
</details>
</li>
<li>
<details><summary><i>Sintaxis Spread</i></summary>
<p>

La sintaxis de spread nos permite expandir un iterable o un objeto en otro lugar dónde se espere esa información. Para poder utilizarlo, necesitamos utilizar los tres puntos suspensivos `...` justo antes.

```js
const networks = ['Twitter', 'Twitch', 'Instagram']
const newNetwork = 'Tik Tok'
// creamos un nuevo array expandiendo el array networks y
// colocando al final el elemento newNetwork
// utilizando la sintaxis de spread
const allNetworks = [...networks, newNetwork]
console.log(allNetworks)
// -> [ 'Twitter', 'Twitch', 'Instagram', 'Tik Tok' ]
```

Esto mismo lo podemos conseguir con un objeto, de forma que podemos expander todas sus propiedades en otro objeto de forma muy sencilla.

```js
const kape = { name: 'Daniel', twitter: '@kapelu' }
const kapeWithNewInfo = {
  ...kape,
  youtube: 'https://youtube.com/kapelu',
  books: ['Aprende React']
}
console.log(kapeWithNewInfo)
// {
//   name: 'Daniel',
//   twitter: '@kapelu',
//   youtube: 'https://youtube.com/kapelu',
//   books: [ 'Aprende React' ]
// }
```

Es importante notar que esto hace una copia, sí, pero superficial. Si tuviéramos objetos anidados dentro del objeto entonces deberíamos tener en cuenta que podríamos mutar la referencia. Veamos un ejemplo.

```js
const kape = {
  name: 'Daniel',
  twitter: '@kapelu',
  experience: {
    years: 18,
    focus: 'javascript'
  }
}

const kapeWithNewInfo = {
  ...kape,
  youtube: 'https://youtube.com/kapelu',
  books: ['Aprende React']
}

// cambiamos un par de propiedades de la "copia" del objeto
kapeWithNewInfo.name = 'Daniel Ángel'
kapeWithNewInfo.experience.years = 19

// hacemos un console.log del objeto inicial
console.log(kape)

// en la consola veremos que el nombre no se ha modificado
// en el objeto original pero los años de experiencia sí
// ya que hemos mutado la referencia original
// {
//   name: 'Daniel',
//   twitter: '@kapelu',
//   experience: { years: 19, focus: 'javascript' }
// }
```

**¿Por qué es importante**

En React es muy normal tener que añadir nuevos elementos a un array o crear nuevos objetos sin necesidad de mutarlos. El operador Rest nos puede ayudar a conseguir esto. Si no conoces bien el concepto de valor y referencia en JavaScript, sería conveniente que lo repases.

</p>
</details>
</li>
<li>
<details><summary><i>Operador Rest</i></summary>
<p>

La sintaxis `...` hace tiempo que funciona en JavaScript en los parámetros de una función. A esta técnica se le llamaba *parámetros rest* y nos permitía tener un número indefinido de argumentos en una función y poder acceder a ellos después como un array.

```js
function suma(...allArguments) {
  return allArguments.reduce((previous, current) => {
    return previous + current
  })
}
```

Ahora el operador rest también se puede utilizar para agrupar el resto de propiedades un objeto o iterable. Esto puede ser útil para extraer un elemento en concreto del objeto o el iterable y crear una copia superficial del resto en una nueva variable.

```js
const kape = {
  name: 'Daniel',
  twitter: '@kapelu',
  experience: {
    years: 18,
    focus: 'javascript'
  }
}

const {name, ...restOfkape} = kape

console.log(restOfkape)
// -> {
//   twitter: '@kapelu',
//   experience: {
//     years: 18,
//     focus: 'javascript'
//   }
// }
```

También podría funcionar con arrays:

```js
const [firstNumber, ...restOfNumbers] = [1, 2, 3]
console.log(firstNumber) // -> 1
console.log(restOfNumbers) // -> [2, 3]
```

**¿Por qué es importante**

Es una forma interesante de *eliminar* (de forma figurada) una propiedad de un objeto y creando una copia superficial del resto de propiedades. A veces puede ser interesante para extraer la información que queremos de unos parámetros y dejar el resto en un objeto que pasaremos hacia otro nivel.

</p>
</details>
</li>
<li>
<details><summary><i>Encadenamiento opcional (Optional Chaining)</i></summary>
<p>
El operador de encadenamiento opcional `?.` te permite leer con seguridad el valor de una propiedad que está anidada dentro de diferentes niveles de un objeto.

De esta forma, en lugar de revisar si las propiedades existen para poder acceder a ellas, lo que hacemos es usar el encadenamiento opcional.

```js
const author = {
  name: 'Daniel',
  libro: {
    name: 'Aprendiendo React'
  },
  writeBook() {
    return 'Writing!'
  }
};

// sin optional chaining
(author === null || author === undefined)
    ? undefined
    : (author.libro === null || author.libro === undefined)
    ? undefined
    : author.libro.name 

// con optional chaining
author?.libro?.name
```

**¿Por qué es importante**

Un objeto es una estructura de datos que es perfecta a la hora de representar muchos elementos de la UI. ¿Tienes un artículo? Toda la información de un artículo seguramente la tendrás representada en un objeto.

Conforme tu UI sea más grande y compleja, estos objetos tendrán más información y necesitarás dominar el encadenamiento opcional `?.` para poder acceder a su información con garantías.

</p>
</details>
<br>
</ol>
</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué es React?</i></summary>
<p>

**React es una biblioteca de JavaScript de código abierto para construir interfaces de usuario.** Está basada en la componetización de la UI: la interfaz se divide en componentes independientes, que contienen su propio estado. Cuando el estado de un componente cambia, React vuelve a renderizar la interfaz.

Esto hace que React sea una herramienta muy útil para construir interfaces complejas, ya que permite dividir la interfaz en piezas más pequeñas y reutilizables.

Fue creada en 2011 por Jordan Walke, un ingeniero de software que trabajaba en Facebook y que quería simplificar la forma de crear interfaces de usuario complejas.

Es una biblioteca muy popular y es usada por muchas empresas como Facebook, Netflix, Airbnb, Twitter, Instagram, etc.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cuáles son las características principales de React?</i></summary>
<p>

Las características principales de React son:

- **Componentes**: React está basado en la componetización de la UI. La interfaz se divide en componentes independientes, que contienen su propio estado. Cuando el estado de un componente cambia, React vuelve a renderizar la interfaz.

- **Virtual DOM**: React usa un DOM virtual para renderizar los componentes. El DOM virtual es una representación en memoria del DOM real. Cuando el estado de un componente cambia, React vuelve a renderizar la interfaz. En lugar de modificar el DOM real, React modifica el DOM virtual y, a continuación, compara el DOM virtual con el DOM real. De esta forma, React sabe qué cambios se deben aplicar al DOM real.

- **Declarativo**: React es declarativo, lo que significa que no se especifica cómo se debe realizar una tarea, sino qué se debe realizar. Esto hace que el código sea más fácil de entender y de mantener.

- **Unidireccional**: React es unidireccional, lo que significa que los datos fluyen en una sola dirección. Los datos fluyen de los componentes padres a los componentes hijos.

- **Universal**: React se puede ejecutar tanto en el cliente como en el servidor. Además, puedes usar React Native para crear aplicaciones nativas para Android e iOS.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué significa exactamente que sea declarativo?</i></summary>
<p>

No le decimos cómo debe renderizar la interfaz a base de instrucciones. Le decimos qué debe renderizar y React se encarga de renderizarlo.

Un ejemplo entre declarativo e imperativo:

```js
// Declarativo
const element = <h1>Hello, world</h1>

// Imperativo
const element = document.createElement('h1')
element.innerHTML = 'Hello, world'
```
</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué es un componente?</i></summary>
<p>

Un componente es una pieza de código que renderiza una parte de la interfaz. Los componentes pueden ser parametrizados, reutilizados y pueden contener su propio estado.

En React los componentes se crean usando funciones o clases.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué es JSX?</i></summary>
<p>

React usa JSX para declarar qué debe renderizar. JSX es una extensión de JavaScript que permite escribir un código más cercano visualmente a HTML, que mejora la legibilidad del código y hace que sea más fácil de entender.

Sin JSX, deberíamos usar `React.createElement` para crear los elementos de la interfaz manualmente de esta forma:

```js
import { createElement } from 'react'

function Hello () { // un componente es una función! 👀
  return React.createElement(
    'h1', // elemento a renderizar
     null, // atributos del elemento
    'Hola Mundo 👋🌍!' // contenido del elemento
  )
}
```

Esto es muy tedioso y poco legible. Por eso, React usa JSX para declarar qué debe renderizar. Por eso usamos JSX de esta forma:

```jsx
function Hello () {
  return <h1>Hola Mundo 👋🌍!</h1>
}
```

Ambos códigos son equivalentes.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cómo se transforma el JSX?</i></summary>
<p>

**El JSX se transforma en código JavaScript compatible en el navegador usando un *transpilador* o *compilador***. El más famoso es a día de hoy Babel, que utiliza una serie de plugins para ser compatible con la transformación, pero existen otros como SWC.

Puedes ver cómo se transforma el JSX en el [playground de código de Babel](https://babeljs.io/repl/#?browsers=defaults%2C%20not%20ie%2011%2C%20not%20ie_mob%2011&build=&builtIns=false&corejs=3.21&spec=false&loose=false&code_lz=GYVwdgxgLglg9mABACQKYBt10QCgJSIDeAUIogE6pQjlIA8AFgIwB8yc6AhogLLgAm2QLwbgaR3APBuBYfYCEdAPTMWxAL5A&debug=false&forceAllTransforms=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=env%2Creact%2Cstage-2&prettier=false&targets=&version=7.19.5&externalPlugins=&assumptions=%7B%7D).

Hay casos especiales en los que un transpilador no es necesario. Por ejemplo, **Deno tiene soporte nativo para la sintaxis JSX** y no es necesario transformar el código para hacerlo compatible.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cuál es la diferencia entre componente y elemento en React?</i></summary>
<p>

Un componente es una función o clase que recibe props y devuelve un elemento.
Un elemento es un objeto que representa un nodo del DOM o una instancia de un componente de React.

```js
// Elemento que representa un nodo del DOM
{
  type: 'button',
  props: {
    className: 'button button-blue',
    children: {
      type: 'b',
      props: {
        children: 'OK!'
      }
    }
  }
}

// Elemento que representa una instancia de un componente
{
  type: Button,
  props: {
    color: 'blue',
    children: 'OK!'
  }
}
```

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cómo crear un componente en React?</i></summary>
<p>

Los componentes en React son funciones o clases que devuelven un elemento de React. Hoy en día lo más recomendado es usar funciones:

```jsx
function HelloWorld() {
  return <h1>Hello World!</h1>
}
```

Pero también puedes usar una clase para crear un componente React:

```jsx
import { Component } from 'react'

class HelloWorld extends Component {
  render() {
    return <h1>Hello World!</h1>
  }
}
```

Lo importante es que el nombre de la función o clase empiece con una letra mayúscula. Esto es necesario para que React pueda distinguir entre componentes y elementos HTML.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué son las props en React?</i></summary>
<p>

Las props son las propiedades de un componente. Son datos que se pasan de un componente a otro. Por ejemplo, si tienes un componente `Button` que muestra un botón, puedes pasarle una prop `text` para que el botón muestre ese texto:

```jsx
function Button(props) {
  return <button>{props.text}</button>
}
```

Podríamos entender que el componente `Button` es un botón genérico, y que la prop `text` es el texto que se muestra en el botón. Así estamos creando un componente reutilizable.

Debe considerarse además que al usar cualquier expresión JavaScript dentro de JSX debe envolverlos con `{}`, en este caso el objeto `props`, de otra forma JSX lo considerará como texto plano.

Para usarlo, indicamos el nombre del componente y le pasamos las props que queremos:

```jsx
<Button text="Haz clic aquí" />
<Button text="Seguir a @Kapelu" />
```

Las props son una forma de parametrizar nuestros componentes igual que hacemos con las funciones. Podemos pasarle cualquier tipo de dato a un componente, incluso otros componentes.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué diferencia hay entre props y state?</i></summary>
<p>

Las *props* son un objeto que **se pasan como argumentos de un componente padre a un componente hijo**. Son inmutables y no se pueden modificar desde el componente hijo.

El *state* es un valor que **se define dentro de un componente**. Su valor es inmutable (no se puede modificar directamente) pero se puede establecer un valor nuevo del estado para que React vuelva a renderizar el componente.

Así que mientras que tanto *props* como *state* afectan al renderizado del componente, su gestión es diferente.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué es y para qué sirve la prop `children` en React?</i></summary>
<p>

La prop `children` es una prop especial que se pasa a los componentes. Es un objeto que contiene los elementos que envuelve un componente.

Por ejemplo, si tenemos un componente `Card` que muestra una tarjeta con un título y un contenido, podemos usar la prop `children` para mostrar el contenido:

```jsx
function Card(props) {
  return (
    <div className="card">
      <h2>{props.title}</h2>
      <div>{props.children}</div>
    </div>
  )
}
```

Y luego podemos usarlo de la siguiente forma:

```jsx
<Card title="Título de la tarjeta">
  <p>Contenido de la tarjeta</p>
</Card>
```

En este caso, la prop `children` contiene el elemento `<p>Contenido de la tarjeta</p>`.

Conocer y saber usar la prop `children` es muy importante para crear componentes reutilizables en React.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Se puede inicializar un estado con el valor de una prop? ¿Qué pasa si lo haces y qué hay que tener en cuenta?</i></summary>
<p>

Sí, se puede inicializar el estado con el valor de una prop. Pero hay que tener en cuenta que, si la prop cambia, el estado no se actualizará automáticamente. Esto es porque el estado se inicializa una vez, cuando el componente se monta por primera vez.

Por ejemplo, con componentes funcionales:

```jsx
const Counter = () => {
  const [count, setCount] = useState(0)

  return (
    <div>
      <Count count={count} />
      <button onClick={() => setCount(count + 1)}>Aumentar</button>
    </div>
  )
}

const Count = ({ count }) => {
  const [number, setNumber] = useState(count)

  return <p>{number}</p>
}
```

En este caso, el componente `Count` inicializa su estado con el valor de la prop `count`. Pero si cambia el valor de la prop `count`, el estado no se actualizará automáticamente. Por lo que al hacer click, siempre veremos el número 0 en pantalla.
POR EJEMPLO:

```jsx
import * as React from 'react';
import { useState } from 'react';
import './style.css';

const Counter = () => {
  const [count, setCount] = useState(0);

  return (
    <div>
      <Count count={count} />
      <button onClick={() => setCount(count + 1)}>Aumentar</button>
    </div>
  );
};

const Count = ({ count }) => {
  const [number, setNumber] = useState(count);

  return <p>{number}</p>;
};

export default function App() {
  return (
    <div>
      <Counter />
    </div>
  );
}
```

En este ejemplo, lo mejor sería simplemente usar la prop `count` en el componente `Count` y así siempre se volvería a renderizar.

**Es una buena práctica evitar al máximo los estados de nuestros componentes y, siempre que se pueda, simplemente calcular el valor a mostrar a partir de las props.**

En el caso que necesites inicializar un estado con una prop, es una buena práctica es añadir el prefijo de `initial` a la prop para indicar que es el valor inicial del estado y que luego no lo usaremos más:

```jsx
const Input = ({ initialValue }) => {
  const [value, setValue] = useState(initialValue)

  return (
    <input
      value={value}
      onChange={e => setValue(e.target.value)}
    />
  )
}
```

Es un error muy común pensar que la prop actualizará el estado, así que tenlo en cuenta.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué es el renderizado condicional en React?</i></summary>
<p>

El renderizado condicional es la forma de mostrar un componente u otro dependiendo de una condición.

Para hacer renderizado condicional en React usamos el operador ternario:

```jsx
function Button({ text }) {
  return text
    ? <button>{text}</button>
    : null
}
```

En este caso, si la prop `text` existe, se renderiza el botón. Si no existe, no se renderiza nada.

Es común encontrar implementaciones del renderizado condicional con el operador &&, del tipo:
```jsx
function List({ listArray }) {
  return listArray?.length && listArray.map(item=>item)
}
```

Tiene sentido, si el length es positivo (mayor a cero) renderizamos el map. !Pues no! ❌ Cuidado, si tiene length de cero, el resultado en el navegador sera un 0. Es preferible utilizar el operador ternario, Kent C. Dodds tiene un articulo interesante hablando del tema. [Use ternaries rather than && in JSX](https://kentcdodds.com/blog/use-ternaries-rather-than-and-and-in-jsx)

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cómo puedes aplicar clases CSS a un componente en React y por qué no se puede usar <strong>class</strong>?</i></summary>
<p>

Para aplicar clases CSS a un componente en React usamos la prop `className`:

```jsx
function Button({ text }) {
  return (
    <button className="button">
      {text}
    </button>
  )
}
```

La razón por la que se llama `className` es porque `class` es una palabra reservada en JavaScript. Por eso, en JSX, tenemos que usar `className` para aplicar clases CSS.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cómo puedes aplicar estilos en línea a un componente en React?</i></summary>
<p>

Para aplicar estilos CSS en línea a un componente en React usamos la prop `style`. La diferencia de cómo lo haríamos con HTML, es que en React los estilos se pasan como un objeto y no como una cadena de texto (esto puede verse más claro con los dobles corchetes, los primeros para indicar que es una expresión JavaScript, y los segundos para crear el objeto):

```jsx
function Button({ text }) {
  return (
    <button style={{ color: 'red', borderRadius: '2px' }}>
      {text}
    </button>
  )
}
```

Fíjate que, además, los nombres de las propiedades CSS están en camelCase.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cómo puedo aplicar estilos de forma condicional a un componente en React?</i></summary>
<p>

Puedes aplicar estilos de forma condicional a un componente en React usando la prop `style` y un operador ternario:

```jsx
function Button({ text, primary }) {
  return (
    <button style={{ color: primary ? 'red' : 'blue' }}>
      {text}
    </button>
  )
}
```

En el caso anterior, si la prop `primary` es `true`, el botón tendrá el color rojo. Si no, tendrá el color azul.

También puedes seguir la misma mecánica usando clases. En este caso, usamos el operador ternario para decidir si añadir o no la clase:

```jsx
function Button({ text, primary }) {
  return (
    <button className={primary ? 'button-primary' : ''}>
      {text}
    </button>
  )
}
```

También podemos usar bibliotecas como `classnames`:

```jsx
import classnames from 'classnames'

function Button({ text, primary }) {
  return (
    <button className={classnames('button', { primary })}>
      {text}
    </button>
  )
}
```

En este caso, si la prop `primary` es `true`, se añadirá la clase `primary` al botón. Si no, no se añadirá. En cambio la clase `button` siempre se añadirá.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué es el renderizado de listas en React?</i></summary>
<p>

El renderizado de listas es la forma de iterar un array de elementos y renderizar elementos de React para cada uno de ellos.

Para hacer renderizado de listas en React usamos el método `map` de los arrays:

```jsx
function List({ items }) {
  return (
    <ul>
      {items.map(item => (
        <li key={item.id}>{item}</li>
      ))}
    </ul>
  )
}
```

En este caso, se renderiza una lista de elementos usando el componente `List`. El componente `List` recibe una prop `items` que es un array de strings. El componente `List` renderiza un elemento `li` por cada elemento del array.

El elemento `li` tiene una prop `key` que es un identificador único para cada elemento. Esto es necesario para que React pueda identificar cada elemento de la lista y actualizarlo de forma eficiente. Más adelante hay una explicación más detallada sobre esto.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cómo puedes escribir comentarios en React?</i></summary>
<p>

Si vas a escribir un comentario fuera del renderizado de un componente, puedes usar la sintaxis de comentarios de JavaScript sin problemas:

```jsx
function Button({ text }) {
  // Esto es un comentario
  /* Esto es un comentario
  de varias líneas */

  return (
    <button>
      {text}
    </button>
  )
}
```

Si vas a escribir un comentario dentro del renderizado de un componente, debes envolver el comentario en llaves y usar siempre la sintaxis de comentarios de bloque:

```jsx
function Button({ text }) {
  return (
    <button>
      {/* Esto es un comentario en el render */}
      {text}
    </button>
  )
}
```

</p>
</details>
</li>
<br>

---

<li>
<details><summary><i>¿Cómo añadir un evento a un componente en React?</i></summary>
<p>

Para añadir un evento a un componente en React usamos la sintaxis `on` y el nombre del evento nativo del navegador en *camelCase*:

```jsx
function Button({ text, onClick }) {
  return (
    <button onClick={onClick}>
      {text}
    </button>
  )
}
```

En este caso, el componente `Button` recibe una prop `onClick` que es una función. Cuando el usuario hace clic en el botón, se ejecuta la función `onClick`.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cómo puedo pasar un parámetro a una función que maneja un evento en React?</i></summary>
<p>

Para pasar un parámetro a una función que maneja un evento en React podemos usar una función anónima:

```jsx
function Button({ id, text, onClick }) {
  return (
    <button onClick={() => onClick(id)}>
      {text}
    </button>
  )
}
```

Cuando el usuario hace clic en el botón, se ejecuta la función `onClick` pasándole como parámetro el valor de la prop `id`.

También puedes crear una función que ejecuta la función `onClick` pasándole el valor de la prop `id`:

```jsx
function Button({ id, text, onClick }) {
  const handleClick = (event) => { // handleClick recibe el evento original
    onClick(id)
  }

  return (
    <button onClick={handleClick}>
      {text}
    </button>
  )
}
```

</p>
</details>
</li>
<br>

---

<li>
<details><summary><i>¿Qué es el estado en React?</i></summary>
<p>

El estado es un objeto que contiene datos que pueden cambiar en el tiempo. En React, el estado se usa para controlar los cambios en la interfaz.

Para que entiendas el concepto, piensa en el interruptor de una habitación. Estos interruptores suelen tener dos estados: encendido y apagado. Cuando accionamos el interruptor y lo ponemos en `on` entonces la luz se enciende y cuando lo ponemos en `off` la luz se apaga.

Este mismo concepto se puede aplicar a la interfaz de usuario. Por ejemplo, el botón Me Gusta de Facebook tendría el estado de `meGusta` a `true` cuando el usuario le ha dado a Me Gusta y a `false` cuando no lo ha hecho.

No solo podemos tener en el estado valores booleanos, también podemos tener objetos, arrays, números, etc.

Por ejemplo, si tienes un componente `Counter` que muestra un contador, puedes usar el estado para controlar el valor del contador.

Para crear un estado en React usamos el hook `useState`:

```jsx
import { useState } from 'react'

function Counter() {
  const [count, setCount] = useState(0)

  return (
    <div>
      <p>Contador: {count}</p>
      <button onClick={() => setCount(count + 1)}>Aumentar</button>
    </div>
  )
}
```

Al usar el hook `useState` este devolverá un `array` de dos posiciones:

0. El valor del estado.
1. La función para cambiar el estado.

Suele usarse desestructuración para facilitar la lectura y ahorrarnos algunas lineas de código. Por otro lado, al pasarle un dato como parámetro al `useState` le estamos indicamos su estado inicial.

Con un componente de clase, la creación del estado sería así:

```jsx
import { Component } from 'react'

class Counter extends Component {
  constructor(props) {
    super(props)
    this.state = { count: 0 }
  }

  render() {
    return (
      <div>
        <p>Contador: {this.state.count}</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Aumentar
        </button>
      </div>
    )
  }
}
```

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué son los hooks?</i></summary>
<p>

Los Hooks son una API de React que nos permite tener estado, y otras características de React, en los componentes creados con una function.

Esto, antes, no era posible y nos obligaba a crear un componente con `class` para poder acceder a todas las posibilidades de la librería.

Hooks es gancho y, precisamente, lo que hacen, es que te permiten enganchar tus componentes funcionales a todas las características que ofrece React.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué hace el hook <strong>useState</strong>?</i></summary>
<p>

El hook `useState` es utilizado para crear variables de estado, quiere decir que su valor es dinámico, que este puede cambiar en el tiempo y eso requiere una re-renderización del componente donde se utiliza

Recibe un parámetro:

- El valor inicial de nuestra variable de estado.

Devuelve un array con dos variables:

- En primer lugar tenemos la variable que contiene el valor
- La siguiente variable es una función set, requiere el nuevo valor del estado, y este modifica el valor de la variable que anteriormente mencionamos
- Cabe destacar que la función proporciona cómo parametro el valor actual del propio estado. Ex: `setIsOpen(isOpen => !isOpen)`

En este ejemplo mostramos como el valor de `count` se inicializa en 0, y también se renderiza cada vez que el valor es modificado con la función `setCount` en el evento `onClick` del button:

```jsx
import { useState } from 'react'

function Counter() {
  const [count, setCount] = useState(0)

  return (
    <>
      <p>Contador: {count}</p>
      <button onClick={() => setCount(count => count + 1)}>Aumentar</button>
    </>
  )
}
```


</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué significa la expresión "subir el estado"?</i></summary>
<p>

Cuando varios componentes necesitan compartir los mismos datos de un estado, entonces se recomienda elevar ese estado compartido hasta su ancestro común más cercano.

Dicho de otra forma. Si dos componentes hijos comparten los mismos datos de su padre, entonces mueve el estado al padre en lugar de mantener un estado local en sus hijos.

Para entenderlo, lo mejor es que lo veamos con un ejemplo. Imagina que tenemos una lista de regalos deseados y queremos poder añadir regalos y mostrar el total de regalos que hay en la lista.

```jsx
import { useState } from 'react'

export default function App () {
  return (
    <>
      <h1>Lista de regalos</h1>
      <GiftList />
      <TotalGifts />
    </>
  )
}

function GiftList () {
  const [gifts, setGifts] = useState([])

  const addGift = () => {
    const newGift = prompt('¿Qué regalo quieres añadir?')
    setGifts([...gifts, newGift])
  }

  return (
    <>
      <h2>Regalos</h2>
      <ul>
        {gifts.map(gift => (
          <li key={gift}>{gift}</li>
        ))}
      </ul>
      <button onClick={addGift}>Añadir regalo</button>
    </>
  )
}

function TotalGifts () {
  const [totalGifts, setTotalGifts] = useState(0)

  return (
    <>
      <h2>Total de regalos</h2>
      <p>{totalGifts}</p>
    </>
  )
}
```

¿Qué pasa si queremos que el total de regalos se actualice cada vez que añadimos un regalo? Como podemos ver, no es posible porque el estado de `totalGifts` está en el componente `TotalGifts` y no en el componente `GiftList`. Y como no podemos acceder al estado de `GiftList` desde `TotalGifts`, no podemos actualizar el estado de `totalGifts` cuando añadimos un regalo.

Tenemos que subir el estado de `gifts` al componente padre `App` y le pasaremos el número de regalos como prop al componente `TotalGifts`.

```jsx
import { useState } from 'react'

export default function App () {
  const [gifts, setGifts] = useState([])

  const addGift = () => {
    const newGift = prompt('¿Qué regalo quieres añadir?')
    setGifts([...gifts, newGift])
  }

  return (
    <>
      <h1>Lista de regalos</h1>
      <GiftList gifts={gifts} addGift={addGift} />
      <TotalGifts totalGifts={gifts.length} />
    </>
  )
}

function GiftList ({ gifts, addGift }) {
  return (
    <>
      <h2>Regalos</h2>
      <ul>
        {gifts.map(gift => (
          <li key={gift}>{gift}</li>
        ))}
      </ul>
      <button onClick={addGift}>Añadir regalo</button>
    </>
  )
}

function TotalGifts ({ totalGifts }) {
  return (
    <>
      <h2>Total de regalos</h2>
      <p>{totalGifts}</p>
    </>
  )
}
```

Con esto, lo que hemos hecho es *elevar el estado*. Lo hemos movido desde el componente `GiftList` al componente `App`. Ahora pasamos como prop los regalos al componente `GiftList` y una forma de actualizar el estado, y también hemos pasado como prop al componente `TotalGifts` el número de regalos.
<br>

- [Código de ejemplo](https://stackblitz.com/edit/react-ts-qitkys?file=App.tsx)

</p>
</details>
</li>
<br>

---

<li>
<details><summary><i>¿Qué hace el hook <strong>useEffect</strong>?</i></summary>
<p>

El hook `useEffect` se usa para ejecutar código cuando se renderiza el componente o cuando cambian las dependencias del efecto.

Recibe dos parámetros:

- La función que se ejecutará al cambiar las dependencias o al renderizar el componente.
- Un array de dependencias. Si cambia el valor de alguna dependencia, ejecutará la función.

En este ejemplo mostramos un mensaje en consola cuando carga el componente y cada vez que cambia el valor de `count`:

```jsx
import { useEffect, useState } from 'react'

function Counter() {
  const [count, setCount] = useState(0)

  useEffect(() => {
    console.log('El contador se ha actualizado')
  }, [count])

  return (
    <>
      <p>Contador: {count}</p>
      <button onClick={() => setCount(count + 1)}>Aumentar</button>
    </>
  )
}
```

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>Explica casos de uso del hook <strong>useEffect</strong></i></summary>
<p>

Podemos usar el hook `useEffect` de diferentes formas, tales como:

- Ejecutar código cuando se renderiza el componente, cuando cambian las dependencias del efecto o cuando se desmonta el componente.
- Por eso puede ser útil para hacer llamadas a APIs, ya que sea nada más montar el componente o cuando cambian las dependencias.
- Realizar tracking de eventos, como Google Analytics, para saber qué páginas visitan los usuarios.
- Podemos validar un formulario para que cada vez que cambie el estado, podamos actualizar la UI y mostrar dónde están los errores.
- Podemos suscribirnos a eventos del navegador, como por ejemplo el evento `resize` para saber cuando el usuario cambia el tamaño de la ventana.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cómo suscribirse a un evento en <strong>useEffect</strong>?</i></summary>
<p>

Dentro de `useEffect` nos podemos suscribir a eventos del navegador, como el evento `resize` para saber cuando el usuario cambia el tamaño de la ventana. Es importante que nos desuscribamos cuando el componente se desmonte para evitar fugas de memoria. Para ello, tenemos que devolver una función dentro del `useEffect` que se ejecutará cuando el componente se desmonte.

```jsx
import { useEffect } from 'react'

function Window() {
  useEffect(() => {
    const handleResize = () => {
      console.log('La ventana se ha redimensionado')
    }

    window.addEventListener('resize', handleResize)

    return () => {
      window.removeEventListener('resize', handleResize)
    }
  }, [])

  return (
    <p>Abre la consola y redimensiona la ventana</p>
  )
}
```

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué hace el hook <strong>useId</strong>?</i></summary>
<p>

`useId` es un hook para generar identificadores únicos que se pueden pasar a los atributos de las etiquetas HTML y es especialmente útil para accesibilidad.

Llama `useId` en el nivel superior del componente para generar una ID única:

```jsx
import { useId } from 'react'
function PasswordField() {
  const passwordHintId = useId()
  // ...
```

A continuación, pasa el ID generado a diferentes atributos:

```jsx
<>
  <input type="password" aria-describedby={passwordHintId} />
  <p id={passwordHintId}>
</>
```

La etiqueta `aria-describedby` te permite especificar que dos etiquetas están relacionadas entre sí, puede generar una identificación única con useId donde incluso si `PasswordField` aparece varias veces en la pantalla, las identificaciones generadas no chocarán.

El ejemplo completo sería así:

```jsx
import { useId } from 'react'

function PasswordField() {
  const passwordHintId = useId()

  return (
    <>
      <label>
        Password:
        <input
          type="password"
          aria-describedby={passwordHintId}
        />
      </label>
      <p id={passwordHintId}>
        El password debe ser de 18 letras y contener caracteres especiales
      </p>
    </>
  )
}

export default function App() {
  return (
    <>
      <h2>Choose password</h2>
      <PasswordField />
      <h2>Confirm password</h2>
      <PasswordField />
    </>
  )
}
```

Como ves en `App` estamos usando el componente dos veces. Si pusieramos una id a mano, por ejemplo `password`, entonces la ID no sería única y quedaría duplicada. Por eso es importante que generes la ID automáticamente con `useId`.

</p>
</details>
</li>
<br>

---

<li>
<details><summary><i>¿Cómo podemos ejecutar código cuando el componente se monta?</i></summary>
<p>

Podemos ejecutar código cuando el componente se monta usando el hook `useEffect` sin pasarle ninguna dependencia. En este caso, la función que se pasa como primer parámetro se ejecutará cuando el componente se monte.

```jsx
import { useEffect } from 'react'

function Component() {
  useEffect(() => {
    console.log('El componente se ha montado')
  }, [])

  return (
    <p>Abre la consola y re-dimensiona la ventana</p>
  )
}
```

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué son los Fragments en React?</i></summary>
<p>

Los Fragments son una forma de agrupar elementos sin añadir un elemento extra al DOM, ya que React no permite devolver varios elementos en un componente, solo un elemento raíz.

Para crear un Fragment en React usamos el componente `Fragment`:

```jsx
import { Fragment } from 'react'

function App() {
  return (
    <Fragment>
      <h1>Titulo</h1>
      <p>Párrafo</p>
    </Fragment>
  )
}
```

También podemos usar la sintaxis de abreviatura:

```jsx
function App() {
  return (
    <>
      <h1>Titulo</h1>
      <p>Párrafo</p>
    </>
  )
}
```

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Por qué es recomendable usar Fragment en vez de un div?</i></summary>
<p>

Las razones por las que es recomendable usar Fragment en vez de un `div` a la hora de envolver varios elementos son:

- Los `div` añaden un elemento extra al DOM, mientras que los Fragments no. Esto hace que el número de elementos HTML y la profundidad del DOM sea menor.
- Los elementos envueltos con Fragment son afectados directamente por las propiedades *flex* o *grid* de CSS de su elemento padre. Si usas un `div` es posible que tengas problemas con el alineamiento de los elementos.
- Los Fragments son más rápidos que los `div` ya que no tienen que ser renderizados.
- Los `div` aplican CSS por defecto (hace que lo que envuelve el `div` se comporte como un bloque al aplicar un `display: block`) mientras que los Fragment no aplican ningún estilo por defecto.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué es el Compound Components Pattern?</i></summary>
<p>

Es un patrón de diseño de componentes que se basa en crear un componente padre con un solo objetivo, proporcionarle a sus hijos las propiedades necesarias para que se rendericen sin problemas.

Permite una estructura declarativa a la hora de construir nuevos componentes, además ayuda a la lectura del código por su simplicidad y limpieza.

Un ejemplo de este diseño sería una lista que renderiza los elementos hijos:

```jsx
<List>
  <ListItem>Cat</ListItem>
  <ListItem>Dog</ListItem>
</List>
```

```jsx
const List = ({ children, ...props }) => (
  <ul {...props} >
    {children}
  </ul>
);

const ListItem = ({ children, ...props }) => {

  return (
    <li {...props}>
      {children}
    </li>
  );
};

export { List, ListItem };
```

Este es un ejemplo sencillo, pero los componentes pueden ser tan complejos como quieras y tanto el padre como los hijos pueden tener sus propios estados.

Enlaces de interés:

- [Lleva tu React al siguiente nivel con Compound Pattern by dezkareid en el blog de Platzi](https://platzi.com/blog/lleva-tu-react-al-siguiente-nivel-con-compound-pattern/?utm_source=twitter&utm_medium=organic&utm_campaign=PLA_TW_BLOG_202205_react_compound_pattern)

- [Compound Components by Jenna Smith](https://jjenzz.com/compound-components) <strong>en inglés</strong>
- [Compound Components Lesson by Kent C. Dodds](https://egghead.io/lessons/react-write-compound-components) <strong>en inglés</strong>

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cómo puedes inicializar un proyecto de React desde cero?</i></summary>
<p>

Existen diversas formas de inicializar un proyecto de React desde cero. Entre las más populares están:

- [Vite](https://vitejs.dev/guide/#scaffolding-your-first-vite-project)

```bash
npm create vite@latest my-app -- --template react
```

- [Create React App](https://create-react-app.dev/docs/getting-started)

```bash
npx create-react-app my-app
```

> La opción más popular y recomendada hoy en día es Vite. <small>Fuente [npm trends](https://npmtrends.com/@vitejs/plugin-react-vs-create-react-app).</small>

Usando un Framework, entre las más populares están:

- [Nextjs](https://nextjs.org/docs/getting-started)

```bash
npx create-next-app@latest my-app
```

- [Gatsby](https://www.gatsbyjs.com/docs/quick-start/)

```bash
npm init gatsby
```

> La opción más popular y recomendada hoy en día es Nextjs. <small>Fuente [npm trends](https://npmtrends.com/gatsby-vs-next)</small>

Cada uno de ellos es un empaquetador de aplicaciones web. Se encargan de resolver las dependencias de tu proyecto, levantar un entorno de desarrollo que se refresca automáticamente con cada cambio y de empaquetar tu aplicación para producción con todos los archivos estáticos necesarios y mucho más.

</p>
</details>
</li>
<br>

---

<br>
</ol>
</details>




























































---
<h2>Intermedio</h2>
<details><summary><i>👉  &nbsp&nbsp Comenzar</i></summary>

---
<p>
<ol start= '1'>
<li>
<details><summary><i>¿Cuántos <strong>useEffect</strong> puede tener un componente?</i></summary>
<p>

Aunque normalmente los componentes de React solo cuentan con un `useEffect` lo cierto es que podemos tener tantos `useEffect` como queramos en un componente. Cada uno de ellos se ejecutará cuando se renderice el componente o cuando cambien las dependencias del efecto.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cómo podemos ejecutar código cuando el componente se desmonta del árbol?</i></summary>
<p>

Podemos ejecutar código cuando el componente se desmonta usando el hook `useEffect` y dentro devolver una función con el código que queremos ejecutar. En este caso, la función que se pasa como primer parámetro del `useEffect` se ejecutará cuando el componente se monte, y la función que es retornada se ejecutará cuando se desmonte.

```jsx
import { useEffect } from 'react'

function Component() {
  useEffect(() => {
    console.log('El componente se ha montado')

    return () => {
      console.log('El componente se ha desmontado')
    }
  }, [])

  return <h1>Ejemplo</h1>
}
```

Esto es muy útil para limpiar recursos que se hayan creado en el componente, como por ejemplo, eventos del navegador o para cancelar peticiones a APIs.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cómo puedes cancelar una petición a una API en <strong>useEffect</strong> correctamente?</i></summary>
<p>

Cuando hacemos una petición a una API, podemos cancelarla para evitar que se ejecute cuando el componente se desmonte usando `AbortController` como hacemos en este ejemplo:

```jsx
useEffect(() => {
  // Creamos el controlador para abortar la petición
  const controller = new AbortController()
  // Recuperamos la señal del controlador
  const { signal } = controller
  // Hacemos la petición a la API y le pasamos como options la señal
  fetch('https://jsonplaceholder.typicode.com/posts/1', { signal })
    .then(res => res.json())
    .then(json => setMessage(json.title))
    .catch(error => {
      // Si hemos cancelado la petición, la promesa se rechaza
      // con un error de tipo AbortError
      if (error.name !== 'AbortError') {
        console.error(error.message)
      }
    })

  // Si se desmonta el componente, abortamos la petición
  return () => controller.abort()
}, [])
```

Esto también funciona con `axios`:

```jsx
useEffect(() => {
  // Creamos el controlador para abortar la petición
  const controller = new AbortController()
  // Recuperamos la señal del controlador
  const { signal } = controller
  // Hacemos la petición a la API y le pasamos como options la señal
  axios
    .get('https://jsonplaceholder.typicode.com/posts/1', { signal })
    .then(res => setMessage(res.data.title))
    .catch(error => {
      // Si hemos cancelado la petición, la promesa se rechaza
      // con un error de tipo AbortError
      if (error.name !== 'AbortError') {
        console.error(error.message)
      }
    })

  // Si se desmonta el componente, abortamos la petición
  return () => controller.abort()
}, [])
```

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cuáles son las reglas de los hooks en React?</i></summary>
<p>

Los hooks en React tienen dos reglas fundamentales:

- Los hooks solo se pueden usar en componentes funcionales o *custom hooks*.
- Los hooks solo se pueden llamar en el nivel superior de un componente. No se pueden llamar dentro de bucles, condicionales o funciones anidadas.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué diferencia hay entre <strong>useEffect</strong> y <strong>useLayoutEffect</strong>?</i></summary>
<p>

Aunque ambos son muy parecidos, tienen una pequeña diferencia en el momento en el que se ejecutan.

`useLayoutEffect` se ejecuta de forma síncrona inmediatamente después que React haya actualizado completamente el DOM tras el renderizado. Puede ser útil si necesitas recuperar un elemento del DOM y acceder a sus dimensiones o posición en pantalla.

`useEffect` se ejecuta de forma asíncrona tras el renderizado, pero no asegura que el DOM se haya actualizado. Es decir, si necesitas recuperar un elemento del DOM y acceder a sus dimensiones o posición en pantalla, no podrás hacerlo con `useEffect` porque no tienes la garantía de que el DOM se haya actualizado.

Normalmente, el 99% de las veces, vas a querer utilizar `useEffect` y, además, tiene mejor rendimiento, ya que no bloquea el renderizado.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué son mejores los componentes de clase o los componentes funcionales?</i></summary>
<p>

Desde que en *React 16.8.0* se incluyeron los hooks, los componentes de funciones pueden hacer casi todo lo que los componentes de clase.

Aunque no hay una respuesta clara a esta pregunta, normalmente los componentes funcionales son más sencillos de leer y escribir y pueden tener un mejor rendimiento en general.

Además, **los hooks solo se pueden usar en los componentes funcionales**. Esto es importante, ya que con la creación de custom hooks podemos reutilizar la lógica y podría simplificar nuestros componentes.

Por otro lado, los componentes de clase nos permiten usar el ciclo de vida de los componentes, algo que no podemos hacer con los componentes funcionales donde solo podemos usar `useEffect`.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cómo mantener los componentes puros y qué ventajas tiene?</i></summary>
<p>

Los componentes puros son aquellos que no tienen estado y que no tienen efectos secundarios. Esto quiere decir que no tienen ningún tipo de lógica que no sea la de renderizar la interfaz.

Son más fáciles de testear y de mantener. Además, son más fáciles de entender porque no tienen lógica compleja.

Para crear un componente puro en React usamos una function:

```jsx
function Button({ text }) {
  return (
    <button>
      {text}
    </button>
  )
}
```

En este caso, el componente `Button` recibe una prop `text` que es un string. El componente `Button` renderiza un botón con el texto que recibe en la prop `text`.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué es el Server Side Rendering y qué ventajas tiene?</i></summary>
<p>

El *Server Side Rendering* es una técnica que consiste en renderizar el HTML en el servidor y enviarlo al cliente. Esto nos permite que el usuario vea la interfaz de la aplicación antes de que se cargue el JavaScript.

Esta técnica nos permite mejorar la experiencia de usuario y mejorar el SEO de nuestra aplicación.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cómo puedes crear un Server Side Rendering con React desde cero?</i></summary>
<p>

Para crear un Server Side Rendering con React desde cero podemos usar el paquete `react-dom/server` que nos permite renderizar componentes de React en el servidor.

Veamos un ejemplo de cómo crear un Server Side Rendering con React desde cero con Express:

```jsx
import express from 'express'
import React from 'react'
import { renderToString } from 'react-dom/server'

const app = express()

app.get('/', (req, res) => {
  const html = renderToString(<h1>Hola mundo</h1>)
  res.send(html)
})
```

Esto nos devolverá el HTML de la aplicación al acceder a la ruta `/`.

```html
<h1 data-reactroot="">Hola mundo</h1>
```

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Puedes poner un ejemplo de efectos colaterales en React?</i></summary>
<p>

Igual que las funciones en JavaScript, los componentes de React también pueden tener *side effects* (efectos colaterales). Un efecto colateral significa que el componente manipula o lee información que no está dentro de su ámbito.

Aquí puedes ver un ejemplo simple de un componente que tiene un efecto colateral. Un componente que lee y modifica una variable que está fuera del componente. Esto hace que sea imposible saber qué renderizará el componente cada vez que se use, ya que no sabemos el valor que tendrá `count`:

```jsx
let count = 0

function Counter() {
  count = count + 1

  return (
    <p>Contador: {count}</p>
  )
}

export default function Counters() {
  return (
    <>
      <Counter />
      <Counter />
      <Counter />
    </>
  )
```

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué diferencia hay entre componentes controlados y no controlados? ¿Qué ventajas y desventajas tienen?</i></summary>
<p>

A la hora de trabajar con formularios en React, tenemos dos tipos de componentes: los componentes controlados y los componentes no controlados.

Los componentes controlados son aquellos que tienen un estado que controla el valor del componente. Por lo tanto, el valor del componente se actualiza cuando el estado cambia.

La ventaja de este tipo de componentes es que son más fáciles de testear porque no dependen de la interfaz. También nos permiten crear validaciones muy fácilmente. La desventaja es que son más complejos de crear y mantener. Además, pueden tener un peor rendimiento, ya que provocan un re-renderizado cada vez que cambia el valor del input.

Los componentes no controlados son aquellos que no tienen un estado que controle el valor del componente. El estado del componente lo controla el navegador de forma interna. Para conocer el valor del componente, tenemos que leer el valor del DOM.

La ventaja de este tipo de componentes es que se cream de forma muy fácil y no tienes que mantener un estado. Además, el rendimiento es mejor, ya que no tiene que re-renderizarse al cambiar el valor del input. Lo malo es que hay que tratar más con el DOM directamente y crear código imperativo.

```js
// Controlado:
const [value, setValue] = useState('')
const handleChange = () => setValue(event.target.value)

<input type="text" value={value} onChange={handleChange} />

// No controlado:
<input type="text" defaultValue="foo" ref={inputRef} />
// Usamos `inputRef.current.value` para leer el valor del input
```

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué son los High Order Components (HOC)?</i></summary>
<p>

Los High Order Components son funciones que reciben un componente como parámetro y devuelven un componente.

```jsx
function withLayout(Component) {
  return function(props) {
    return <main>
      <section>
        <Component {...props} />
      </section>
    </main>
  }
}
```

En este caso, la función `withLayout` recibe un componente como parámetro y devuelve un componente. El componente devuelto renderiza el componente que se le pasa como parámetro dentro de un layout.

Es un patrón que nos permite reutilizar código y así podemos inyectar funcionalidad, estilos o cualquier otra cosa a un componente de forma sencilla.

Con la llegada de los hooks, los HOCs se han vuelto menos populares, pero todavía se usan en algunos casos.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué son las render props?</i></summary>
<p>

Son un patrón de diseño de React que nos permite reutilizar código entre componentes e inyectar información en el renderizado de los componentes.

```jsx
<DataProvider render={data => (
  <h1>Hello {data.target}</h1>
)}/>
```

En este caso, el componente `DataProvider` recibe una función `render` como prop. Ahí le indicamos qué es lo que debe renderizar usando la información que recibe como parámetro.

La implementación del `DataProvider` con funciones podría ser la siguiente:

```jsx
function DataProvider({ render }) {
  const data = { target: 'world' }
  return render(data)
}
```

También se puede encontrar este patrón usando la prop `children` en los componentes.

```jsx
<DataProvider>
  {data => (
    <h1>Hello {data.target}</h1>
  )}
</DataProvider>
```

Y la implementación sería similar:

```jsx
function DataProvider({ children }) {
  const data = { target: 'world' }
  return children(data)
}
```

Este patrón es usado por grandes bibliotecas como `react-router`, `formik` o `react-motion`.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Por qué no podemos usar un <strong>if</strong> en el renderizado de un componente?</i></summary>
<p>

En React, no podemos usar un `if` en el renderizado de un componente porque no es una expresión válida de JavaScript, es una declaración. Las expresiones son aquellas que devuelven un valor y las declaraciones no devuelven ningún valor.

En JSX solo podemos usar expresiones, por eso usamos ternarias, que sí son expresiones.

```jsx
// ❌ Esto no funciona
function Button({ text }) {
  return (
    <button>
      {if (text) { return text } else { return 'Click' }}
    </button>
  )
}
```

De la misma forma, tampoco podemos usar `for`, `while` o `switch` dentro del renderizado de un componente.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Por qué debemos utilizar una función para actualizar el estado de React?</i></summary>
<p>

A la hora de actualizar el estado de React, debemos utilizar la función que nos facilita el hook `useState` para actualizar el estado.

```jsx
const [count, setCount] = useState(0)

setCount(count + 1)
```

¿Por qué es esto necesario? En primer lugar, el estado en React debe ser inmutable. Es decir, no podemos modificar el estado directamente, sino que debemos siempre crear un nuevo valor para el nuevo estado.

Esto nos permite que la integridad de la UI respecto a los datos que renderiza siempre es correcta.

Por otro lado, llamar a una función le permite a React saber que el estado ha cambiado y que debe re-renderizar el componente si es necesario. Además esto lo hace de forma asíncrona, por lo que podemos llamar a `setCount` tantas veces como queramos y React se encargará de actualizar el estado cuando lo considere oportuno.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué es el ciclo de vida de un componente en React?</i></summary>
<p>

En los componentes de clase, el ciclo de vida de un componente se divide en tres fases:

- Montaje: cuando el componente se añade al DOM.
- Actualización: cuando el componente se actualiza.
- Desmontaje: cuando el componente se elimina del DOM.

Dentro de este ciclo de vida, existe un conjunto de métodos que se ejecutan en el componente.

Estos métodos se definen en la clase y se ejecutan en el orden que se muestran a continuación:

- constructor
- render
- componentDidMount
- componentDidUpdate
- componentWillUnmount

En cada uno de estos métodos podemos ejecutar código que nos permita controlar el comportamiento de nuestro componente.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Por qué puede ser mala práctica usar el <strong>index</strong> como key en un listado de React?</i></summary>
<p>

Cuando renderizamos una lista de elementos, React necesita saber qué elementos han cambiado, han sido añadidos o eliminados.

Para ello, React necesita una key única para cada elemento de la lista. Si no le pasamos una key, React usa el índice del elemento como key.

```jsx
const List = () => {
  const [items, setItems] = useState(['Item 1', 'Item 2', 'Item 3'])

  return (
    <ul>
      {items.map((item, index) => (
        <li key={index}>{item}</li>
      ))}
    </ul>
  )
}
```

En este caso, React usa el índice del elemento como `key`. Esto puede ser un problema si la lista se reordena o se eliminan elementos del array, ya que el índice de los elementos cambia.

En este caso, React no sabe qué elementos han cambiado y puede que se produzcan errores.

Un ejemplo donde se ve el problema:

```jsx
const List = () => {
  const [items, setItems] = useState(['Item 1', 'Item 2', 'Item 3'])

  const handleRemove = (index) => {
    const newItems = [...items]
    newItems.splice(index, 1)
    setItems(newItems)
  }

  return (
    <ul>
      {items.map((item, index) => (
        <li key={index}>
          {item}
          <button onClick={() => handleRemove(index)}>Eliminar</button>
        </li>
      ))}
    </ul>
  )
}
```
</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Para qué sirve el hook <strong>useMemo</strong>?</i></summary>
<p>

El hook `useMemo` es un hook que nos permite memorizar el resultado de una función. Esto quiere decir que si la función que le pasamos como parámetro no ha cambiado, no se ejecuta de nuevo y se devuelve el resultado que ya se había calculado.

```jsx
import { useMemo } from 'react'

function Counter({ count }) {
  const double = useMemo(() => count * 2, [count])

  return (
    <div>
      <p>Contador: {count}</p>
      <p>Doble: {double}</p>
    </div>
  )
}
```

En este caso, el componente `Counter` recibe una prop `count` que es un número. El componente calcula el doble de ese número y lo muestra en pantalla.

El hook `useMemo` recibe dos parámetros: una función y un array de dependencias. La función se ejecuta cuando el componente se renderiza por primera vez y cuando alguna de las dependencias cambia.

La función se ejecuta cuando el componente se renderiza por primera vez y cuando la prop `count` cambia.

La ventaja es que si la prop `count` no cambia, se evita el cálculo del doble y se devuelve el valor que ya se había calculado previamente.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Es buena idea usar siempre `useMemo` para optimizar nuestros componentes?</i></summary>
<p>

No. `useMemo` es una herramienta que nos permite optimizar nuestros componentes, pero no es una herramienta mágica que nos va a hacer que nuestros componentes sean más rápidos. A veces el cálculo de un valor es tan rápido que no merece la pena memorizarlo. Incluso, en algunos casos, puede ser más lento memorizarlo que calcularlo de nuevo.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Para qué sirve el hook `useCallback`?</i></summary>
<p>

El hook `useCallback` es un hook que nos permite memorizar una función. Esto quiere decir que si la función que le pasamos como parámetro no ha cambiado, no se ejecuta de nuevo y se devuelve la función que ya se había calculado.

```jsx
import { useCallback } from 'react'

function Counter({ count, onIncrement }) {
  const handleIncrement = useCallback(() => {
    onIncrement(count)
  }, [count, onIncrement])

  return (
    <div>
      <p>Contador: {count}</p>
      <button onClick={handleIncrement}>Incrementar</button>
    </div>
  )
}
```

En este caso, el componente `Counter` recibe una prop `count` que es un número y una prop `onIncrement` que es una función que se ejecuta cuando se pulsa el botón.

El hook `useCallback` recibe dos parámetros: una función y un array de dependencias. La función se ejecuta cuando el componente se renderiza por primera vez y cuando alguna de las dependencias cambia.

La función se ejecuta cuando el componente se renderiza por primera vez y cuando la prop `count` o la prop `onIncrement` cambia.

La ventaja es que si la prop `count` o la prop `onIncrement` no cambian, se evita la creación de una nueva función y se devuelve la función que ya se había calculado previamente.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Es buena idea usar siempre `useCallback` para optimizar nuestros componentes?</i></summary>
<p>

No. `useCallback` es una herramienta que nos permite optimizar nuestros componentes, pero no es una herramienta mágica que nos va a hacer que nuestros componentes sean más rápidos. A veces la creación de una función es tan rápida que no merece la pena memorizarla. Incluso, en algunos casos, puede ser más lento memorizarla que crearla de nuevo.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cuál es la diferencia entre `useCallback` y `useMemo`?</i></summary>
<p>

La diferencia entre `useCallback` y `useMemo` es que `useCallback` memoriza una función y `useMemo` memoriza el resultado de una función.

En cualquier caso, en realidad, `useCallback` es una versión especializada de `useMemo`. De hecho se puede simular la funcionalidad de `useCallback` con `useMemo`:

```js
const memoizedCallback = useMemo(() => {
  return () => {
    doSomething(a, b)
  }
}, [a, b])
```

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué es el `StrictMode` en React?</i></summary>
<p>

El `StrictMode` es un componente que nos permite activar algunas comprobaciones de desarrollo en React. Por ejemplo, detecta componentes que se renderizan de forma innecesaria o funcionalidades obsoletas que se están usando.

```jsx
import { StrictMode } from 'react'

function App() {
  return (
    <StrictMode>
      <Component />
    </StrictMode>
  )
}
```

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Por qué es recomendable usar exportar los componentes de React de forma nombrada?</i></summary>
<p>

Los componentes de React se pueden exportar de dos formas:

- Exportación por defecto
- Exportación nombrada

Para exportar un componente por defecto, usamos la palabra reservada `default`:

```jsx
// button.jsx
export default function Button() {
  return <button>Click</button>
}

// App.jsx
import Button from './button.jsx'

function App() {
  return <Button />
}
```

La gran desventaja que tiene la exportación por defecto es que a la hora de importarlo puedes usar cualquier nombre que quieras. Y esto trae problemas, ya que puedes no usar siempre el mismo en el proyecto o usar un nombre que no sea correcto con lo que importas.

```jsx
// button.jsx
export default function Button() {
  return <button>Click</button>
}

// App.jsx
import MiBoton from './button.jsx'

function App() {
  return <MiBoton />
}

// Otro.jsx
import Button from './button.jsx'

function Otro() {
  return <Button />
}
```

Los exports nombrados nos obligan a usar el mismo nombre en todos los archivos y, por tanto, nos aseguramos que siempre estamos usando el nombre correcto.

```jsx
// button.jsx
export function Button() {
  return <button>Click</button>
}

// App.jsx
import { Button } from './button.jsx'

function App() {
  return <Button />
}
```

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cómo puedes exportar múltiples componentes de un mismo archivo?</i></summary>
<p>

Para exportar múltiples componentes de un mismo archivo, podemos usar la exportación nombrada:

```jsx
// button.jsx
export function Button({children}) {
  return <button>{children}</button>
}

export function ButtonSecondary() {
  return <button class="btn-secondary">{children}</button>
}
```

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué es el `SyntheticEvent` en React?</i></summary>
<p>

El `SyntheticEvent` es una abstracción del evento nativo del navegador. Esto le permite a React tener un comportamiento consistente en todos los navegadores.

```jsx
function App() {
  function handleClick(event) {
    console.log(event)
  }

  return <button onClick={handleClick}>Haz clic aquí</button>
}
```

</p>
</details>
</li>
<br>

---
</ol>
</details>

---
<h2>Experto</h2>
<details><summary><i>👉  &nbsp&nbsp Comenzar</i></summary>

---
<p>
<ol start= '1'>
<li>
<details><summary><i>¿Es React una biblioteca o un framework? ¿Por qué?</i></summary>
<p>

Existe una fina línea hoy en día entre qué es una biblioteca o un framework. Oficialmente, React se autodenomina como biblioteca. Esto es porque para poder crear una aplicación completa, necesitas usar otras bibliotecas.

Por ejemplo, *React* no ofrece un sistema de enrutado de aplicaciones oficial. Por ello, hay que usar una biblioteca como [React Router](https://reactrouter.com/) o usar un *framework* como [Next.js](https://nextjs.org/) que ya incluye un sistema de enrutado.

Tampoco puedes usar React para añadir las cabeceras que van en el `<head>` en tu aplicación, y también necesitarás otra biblioteca u framework para solucionar esto.

Otra diferencia es que React no está opinionado sobre qué empaquetador de aplicaciones usar. En cambio `Angular` en su propio tutorial ya te indica que debes usar `@angular/cli` para crear una aplicación, en cambio React siempre te deja la libertad de elegir qué empaquetador usar y ofrece diferentes opciones.

Aún así, existe gente que considera a React como un framework. Aunque no hay una definición oficial de qué es un framework, la mayoría de la gente considera que un framework es una biblioteca que incluye otras bibliotecas para crear una aplicación completa de forma opinionada y casi sin configuración.

Por ejemplo, **Next.js se podría considerar un framework de React** porque incluye React, un sistema de enrutado, un sistema de renderizado del lado del servidor, etc.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Para qué sirve el hook `useImperativeHandle`?</i></summary>
<p>

Nos permite definir qué propiedades y métodos queremos que sean accesibles desde el componente padre.

En el siguiente ejemplo vamos a crear un componente `TextInput` que tiene un método `focus` que cambia el foco al elemento `<input>`.

```jsx
import { useRef, useImperativeHandle } from 'react'

function TextInput(props, ref) {
  const inputEl = useRef(null)

  useImperativeHandle(ref, () => ({
    focus: () => {
      inputEl.current.focus()
    }
  }))

  return (
    <input ref={inputEl} type="text" />
  )
}
```

Creamos una referencia `inputEl` con `useRef` y la pasamos al elemento `<input>` como prop `ref`. Cuando el componente se monta, la referencia `inputEl` apunta al elemento `<input>` del DOM.

Para acceder al elemento del DOM, usamos la propiedad `current` de la referencia.

Para que el componente padre pueda acceder al método `focus`, usamos el hook `useImperativeHandle`. Este hook recibe dos parámetros: una referencia y una función que devuelve un objeto con las propiedades y métodos que queremos que sean accesibles desde el componente padre.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué son los portales en React?</i></summary>
<p>

Los portales nos permiten renderizar un componente en un nodo del DOM que no es hijo del componente que lo renderiza.

Es perfecto para ciertos casos de uso como, por ejemplo, modales:

```jsx
import { createPortal } from 'react-dom'

function Modal() {
  return createPortal(
    <div className="modal">
      <h1>Modal</h1>
    </div>,
    document.getElementById('modal')
  )
}
```

`createPortal` acepta dos parámetros:

- El primer parámetro es el componente que queremos renderizar
- El segundo parámetro es el nodo del DOM donde queremos renderizar el componente

En este caso el modal se renderiza en el nodo `#modal` del DOM.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué problemas crees que pueden aparecer en una aplicación al querer visualizar listas de miles/millones de datos?</i></summary>
<p>

- **Tiempo de respuesta del servidor:** Hacer peticiones de millones de datos no es, en general, una buena estrategía. Incluso en el mejor de los casos, en el que el servidor solo debe devolver los datos sin tratarlos, hay un coste asociado al *parseo* y *envío* de los mismos a través de la red. Llamadas con un tamaño desmesurado pueden incurrir en interfaces lentas, e incluso en *timeouts* en la respuesta.
- **Problemas de rendimiento:** Aunque es cierto que **React** se basa en un modelo *declarativo* en el cual no debemos tener una exhaustivo control o gestión de cómo se *renderiza* no hay que olvidar que malas decisiones técnicas pueden conllevar aplicaciones totalmente inestables incluso con las mejores tecnologías. No es viable *renderizar* un *DOM* con millones de elementos, el *navegador* no podrá gestionarlo y, tarde o temprano, la aplicación no será usable.

 Como developers, nuestra misión es encontrar el equilibrio entre rendimiento y experiencia, intentando priorizar siempre cómo el usuario sentirá la aplicación. No hay ningún caso lo suficientemente justificado para *renderizar* en pantalla miles de datos.

 **El espacio de visualización es limitado (*viewport*), al igual que deberían serlo los datos que añadimos al DOM.**

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué solución/es implementarías para evitar problemas de rendimiento al trabajar con listas de miles/millones de datos?</i></summary>
<p>

### Pagination

En lugar de recibir la lista en una sola llamada a la API (lo cual sería negativo tanto para el rendimiento como para el propio servidor y tiempo de respuesta de la API), podríamos implementar un sistema de paginación en el cual la API recibirá un *offset* o *rango* de datos deseados. En el FE nuestra responsabilidad es mostrar unos controles adecuados (interfaz de paginación) y gestionar las llamadas a petición de cambio de página para siempre limitar la cantidad de DOM renderizado evitando así una sobrecarga del *DOM* y, por lo tanto, problemas de rendimiento.

### Virtualization

Existe una técnica llamada *Virtualización* que gestiona cuantos elementos de una lista mantenemos ***vivos*** en el *DOM*. El concepto se basa en solo montar los elementos que estén dentro del *viewport* más un *buffer* determinado (para evitar falta de datos al hacer scroll) y, en cambio, desmontar del *DOM* todos aquellos elementos que estén fuera de la vista del usuario. De este modo podremos obtener lo mejor de los dos mundos, una experiencia integrada y un DOM liviano que evitará posibles errores de rendimiento. Con esta solución también podremos aprovechar que contamos con los datos en memoria para realizar búsquedas/filtrados sin necesidad de más llamadas al servidor.

Puedes consultar esta librería para aplicar Virtualización con React: [React Virtualized](https://github.com/bvaughn/react-virtualized).

Hay que tener en cuenta que cada caso de uso puede encontrar beneficios y/o perjuicios en ambos métodos, dependiendo de factores como capacidad de respuesta de la API, cantidad de datos, necesidad de filtros complejos, etc. Por ello es importante analizar cada caso con criterio.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué es el hook `useDebugValue`?</i></summary>
<p>

Nos permite mostrar un valor personalizado en la pestaña de *React DevTools* que nos permitirá depurar nuestro código.

```jsx
import { useDebugValue } from 'react'

function useCustomHook() {
  const value = 'custom value'
  useDebugValue(value)
  return value
}
```

En este ejemplo, el valor personalizado que se muestra en la pestaña de *React DevTools* es `custom value`.

Aunque es útil para depurar, no se recomienda usar este hook en producción.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué es el `Profiler` en React?</i></summary>
<p>

El `Profiler` es un componente que nos permite medir el tiempo que tarda en renderizarse un componente y sus hijos.

```jsx
import { Profiler } from 'react'

function App() {
  return (
    <Profiler id="App" onRender={(id, phase, actualDuration) => {
      console.log({id, phase, actualDuration})
    }}>
      <Component />
    </Profiler>
  )
}
```

El componente `Profiler` recibe dos parámetros:

- `id`: es un identificador único para el componente
- `onRender`: es una función que se ejecuta cada vez que el componente se renderiza

Esta información es muy útil para detectar componentes que toman mucho tiempo en renderizarse y optimizarlos.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cómo puedes acceder al evento nativo del navegador en React?</i></summary>
<p>

React no expone el evento nativo del navegador. En su lugar, React crea un objeto sintético que se basa en el evento nativo del navegador llamado `SyntheticEvent`. Para acceder al evento nativo del navegador, debemos usar el atributo `nativeEvent`:

```jsx
function Button({ onClick }) {
  return <button onClick={e => onClick(e.nativeEvent)}>Haz clic aquí</button>
}
```

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cómo puedes registrar un evento en la fase de captura en React?</i></summary>
<p>

En React, los eventos se registran en la fase de burbuja por defecto. Para registrar un evento en la fase de captura, debemos añadir `Capture` al nombre del evento:

```jsx
function Button({ onClick }) {
  return <button onClickCapture={onClick}>Haz clic aquí</button>
}
```

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Cómo puedes mejorar el rendimiento del Server Side Rendering en React para evitar que bloquee el hilo principal?</i></summary>
<p>

Aunque puedes usar el método `renderToString` para renderizar el HTML en el servidor, este método es síncrono y bloquea el hilo principal. Para evitar que bloquee el hilo principal, debemos usar el método `renderToPipeableStream`:

```jsx
let didError = false
const stream = renderToPipeableStream(
  <App />,
  {
    onShellReady() {
      // El contenido por encima de los límites de Suspense ya están listos
      // Si hay un error antes de empezar a hacer stream, mostramos el error adecuado
      res.statusCode = didError ? 500 : 200
      res.setHeader('Content-type', 'text/html')
      stream.pipe(res)
    },
    onShellError(error) {
      // Si algo ha ido mal al renderizar el contenido anterior a los límites de Suspense, lo indicamos.
      res.statusCode = 500
      res.send(
        '<!doctype html><p>Loading...</p><script src="clientrender.js"></script>'
      )
    },
    onAllReady() {
      // Si no quieres hacer streaming de los datos, puedes usar
      // esto en lugar de onShellReady. Esto se ejecuta cuando
      // todo el HTML está listo para ser enviado.
      // Perfecto para crawlers o generación de sitios estáticos

      // res.statusCode = didError ? 500 : 200
      // res.setHeader('Content-type', 'text/html')
      // stream.pipe(res)
    },
    onError(err) {
      didError = true
      console.error(err)
    },
  }
)
```

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué diferencia hay entre <strong>renderToStaticNodeStream()</strong> y <strong>renderToPipeableStream()</strong>?</i></summary>
<p>

`renderToStaticNodeStream()` devuelve un stream de nodos estáticos, esto significa que no añade atributos extras para el DOM que React usa internamente para poder lograr la hidratación del HTML en el cliente. Esto significa que no podrás hacer el HTML interactivo en el cliente, pero puede ser útil para páginas totalmente estáticas.

`renderToPipeableStream()` devuelve un stream de nodos que contienen atributos del DOM extra para que React pueda hidratar el HTML en el cliente. Esto significa que podrás hacer el HTML interactivo en el cliente pero puede ser más lento que `renderToStaticNodeStream()`.
</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Para qué sirve el método `renderToReadableStream()`?</i></summary>
<p>

Este método es similar a `renderToNodeStream`, pero está pensado para entornos que soporten Web Streams como Deno.

Un ejemplo de uso sería el siguiente:

```jsx
const controller = new AbortController()
const { signal } = controller

let didError = false

try {
  const stream = await renderToReadableStream(
    <html>
      <body>Success</body>
    </html>,
    {
      signal,
      onError(error) {
        didError = true
        console.error(error)
      }
    }
  )

  // Si quieres enviar todo el HTML en vez de hacer streaming, puedes usar esta línea
  // Es útil para crawlers o generación estática:
  // await stream.allReady

  return new Response(stream, {
    status: didError ? 500 : 200,
    headers: {'Content-Type': 'text/html'},
  })
} catch (error) {
  return new Response(
    '<!doctype html><p>Loading...</p><script src="clientrender.js"></script>',
    {
      status: 500,
      headers: {'Content-Type': 'text/html'},
    }
  )
}
```

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿Qué es Flux?</i></summary>
<p>

*Flux* es un patrón de arquitectura de aplicaciones que se basa en un unidireccional de datos. En este patrón, los datos fluyen en una sola dirección: de las vistas a los stores.

No es específico de React y se puede usar con cualquier librería de vistas. En este patrón, los stores son los encargados de almacenar los datos de la aplicación. Los stores emiten eventos cuando los datos cambian. Las vistas se suscriben a estos eventos para actualizar los datos.

Esta arquitectura fue creada por Facebook para manejar la complejidad de sus aplicaciones. *Redux* se basó en este patrón para crear una biblioteca de gestión de estado global.
</p>
</details>
</li>
</ol>
</details>