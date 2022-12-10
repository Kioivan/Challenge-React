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
<details><summary><i>¿Cómo puedes aplicar clases CSS a un componente en React?</i></summary>
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
<details><summary><i>¿Cómo puedes inicializar un proyecto de React desde cero?</i></summary>
<p>

Existen diversas formas de inicializar un proyecto de React desde cero. Una de las formas más sencillas es usando [Vite](https://vitejs.dev/guide/#scaffolding-your-first-vite-project).

```bash
npm create vite@latest your-react-app-name -- --template react
```

> Vite es un empaquetador de aplicaciones web. Se encarga de resolver las dependencias de tu proyecto, levantar un entorno de desarrollo que se refresca automáticamente con cada cambio y de empaquetar tu aplicación para producción con todos los archivos estáticos necesarios.


</p>
</details>
</li>
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
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

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
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
<li>
<details><summary><i>¿xxxxxxxxxxxxxxxxxxx?</i></summary>
<p>
Lorem ipsum dolor sit amet. Sed fugit minus ea corrupti distinctio eum voluptatem possimus est tenetur distinctio ab dolor deleniti et quasi iste. Ea optio quae ut officiis molestias id maiores impedit ab nemo odio ut eligendi obcaecati sed sunt magni. Eum quas quasi et aperiam omnis ut officia esse in quaerat tempora nam quia consequatur eum dolore omnis nam ipsa quasi. A labore velit ex impedit quisquam vel porro dolorum ut quia odit est illo eaque? Ut ipsa quia At reiciendis officia sit tempore omnis ad quisquam officiis non internos galisum et omnis iure sit facere nihil. Ut dolore voluptatem id voluptatibus consequuntur est expedita voluptas ut minus magni. At quia iure et cupiditate quia vel eveniet suscipit! Id voluptatem consectetur qui exercitationem eius et velit rerum et galisum unde et quam consequuntur et inventore velit! Sed quis illum a illo quisquam ea error sint est earum nihil. Et eligendi perspiciatis et ducimus error ea rerum harum. Non maxime consectetur qui incidunt dolores ut saepe sapiente quo atque suscipit At voluptas inventore.

</p>
</details>
</li>
<br>

---
</ol>
</details>