13 sept 2019

## Web Development - What is this trying to solve?

- template engine = to solve problem of maintaining the website with multiple pages with consistent data eg. navbar
- server side rendered webpages = server creates the index.html page from other file formats
  - eg. Laravel, Django, Rails 
- React is typically frontend rendered. However there is also server side React
- https://www.webcomponents.org/
- HTTP/2



#### MVC = model view controller

model = gets information from database

view = template engine

controller = logic portion



#### DOM = document object model

- essentially converting html tags into a Javascript manipulatable format



##### CDN = content delivery network



##### Vanilla

```js
//vanilla javascript
const app = document.querySelector("#app");
app.textContent = "Hello";

const h3 = document.createElement("h3");
h3.textContent = "Hello World!";

// app.appendChild(h3);

// jQuery
//("<tags>") = creates a tag
//("tags") = searches through HTML for this tag
// const h1 = $("<h1>").text("Hello, world 2!");
// $("#app").append(h1);

//React
const h2 = React.createElement("h2", null, "Hello, world");
ReactDOM.render(h2, app);
```



##### jQuery

### React

```html
<!-- React--> 
<script
 crossorigin      src="https://unpkg.com/react@16/umd/react.development.js"
></script>

<!-- React DOM--> 
<script
 crossorigin
 src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"
></script>

<!-- Babel--> 
<script src="https://cdnjs.cloudflare.com/ajax/libs/babel-standalone/6.26.0/babel.min.js"></script>

<!-- change the text type from ES6 to JSX--> 
<script type="text/babel" src="app.js"></script>

```

- Babel = converts JS to JSX

  https://reactjs.org/docs/introducing-jsx.html



- Html `class` becomes `className ` in JSX

  - JSX follows the DOM call tags

  ```htm;
  HTML   <h1 class="hello">
  JSX    <h1 className="hello">
  ```



- function component (static) vs class component (dynamic)

  - functions cannot change its value

  - a class component will need a render function which returns JSX
  
    
  
  - function/ class component can only return within 1 wrapper, because only have 1 create element. If it is not within 1 wrapper, it means that we will need a nested CreateElement.
  
  ```
  JSX = <h1>"hi"</h1>
  JS = React.CreateElement('h1', null, "hi")
  ```
  
  
  
  ```react
  const root = document.querySelector("#app");
  
  function Child(props) {
    return (
      <h1>
        Hi my name is {props.name} and I am {props.age}
    </h1>
    );
}
  
class Parent extends React.Component {
    render() {
      return (
        <div>
          <Child name="Alice" age={9} />
          <Child name="Bob" age={5} />
        </div>
      );
    }
  }
  
  ReactDOM.render(<Parent />, root);
  ```



#### React has 2 properties

- ##### State 

  - is stated by you

- ##### Props

  - cannot change them 



- Passing in an array with a .map() to get the {props.title}, {props.author}, {props.date}

