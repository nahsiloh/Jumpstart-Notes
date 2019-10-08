16 sept 2019

## React

- How to set up a React Application - should try from scratch

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



--------------------------------------------------------------------------------------------------------------------------------

##### Difference between using Class components and function components

- Always use function components unless require to change the state.



##### Linking JS scripts

- the browser is unable to process the "require" import that JS uses

- link JS files through the HTML script
- or by React Create App - using the import keyword



##### Fetching data/API

- will require it to be stored "locally first" - thats why need to set in as a state = hence require the use of class constructor 
- lifecycle methodology
- React constantly re-renders the page - thus will require to set the lifecycle of the data using eg. `componentDidMount()`

```react
class Blog extends React.Component {
  constructor() {
    super();
    this.state = { data: [] };
  }

 	//built in function in the React.Component 
  componentDidMount() {
    console.log("Blog component has been mounted");
    fetch(
      "https://my-json-server.typicode.com/thoughtworks-jumpstart/api/posts"
    )
      .then(res => res.json())
      .then(data => {
        console.log("I have fetched the data");
        this.setState({ data });
      });
  }

  render() {
    return this.state.data.map(post => (
      <Post
        key={post.id}
        title={post.title}
        author={post.author}
        date={post.date}
      />
    ));
  }
}
```



#### Lifecycle Methods in React

http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/

![1568608463719](C:\Users\lisha\AppData\Roaming\Typora\typora-user-images\1568608463719.png)



### Create React App

`npx create-react-app <App Name>`



- "start": "react-scripts start" = `npm run start`

  - opens the page in the browser

    

- "build": "react-scripts build" =  `npm run build`

  - compressed version of the src files = for production

    

- "test": "react-scripts test" = `npm run test`
  
  - already has a test in built



```react
// how to create a function within the class component and invoke with the this. keyword

class HelloReact extends React.Component {
  helloReact = () => {
    return "Hello React!";
  };
  render() {
    return <div>{this.helloReact()}</div>;
  }
}

// how to create a function within a function component and invoke it
const GoodByeWorld = () => {
  const goodByeWorld = () => {
    return "Good Bye World";
  };
  return <div>{goodByeWorld()}</div>;
};

```



```react
//should always return a function. Thus, create a function to place all the logic inside before returning 
const ReactGreet = () => {
  const greetReact = ["Hello", "Goodbye"];
  const sayGreetingReact = () => {
    return greetReact.map(greet => <h1>{greet} React!</h1>);
  };
  return <div>{sayGreetingReact()}</div>;
};

```



- All arrays need a unique key = React identifies the key to track if the array changes, to control re-renders

  https://reactjs.org/docs/lists-and-keys.html#keys

```react
class World extends React.Component {
  greetWorld = ["Hello World", "Goodbye World"];
  sayGreetingWorld = () => {
    return this.greetWorld.map(greet => <h1 key={greet}>{greet}</h1>);
  };
  render() {
    return <div>{this.sayGreetingWorld()}</div>;
  }
}
```



```react
World and React World
const MyText = props => {
  return (
    <p className={"my-text rotate"} key={props.text}>
      {"everything change: " + props.text}
    </p>
  );
};

class World extends React.Component {
  getWhatIWannaSay = () => {
    const whatIwantToSay = ["Hello World", "Goodbye World"];
    return whatIwantToSay.map(aPhrase => <MyText text={aPhrase} />);
  };

  render() {
    return <div>{this.getWhatIWannaSay()}</div>;
  }
}
```



##### Importing and exporting

| fileA.js                                                     | fileB.js                                                     |
| :----------------------------------------------------------- | ------------------------------------------------------------ |
| - name need to match  between the imported and exported file<br />- there is a command that allows for auto update in file B if changes were made in File A<br />`export const exportedApple = "Fuji Apple"`<br />`export const thaiDurian = "Thai Durian"` | - file A is imported using the destructure syntax<br />`import{exportedApple, thaiDurian} from "./fileA"`<br />`console.log(exportedApple)`<br />`console.log(thaiDurian)` |
| - when you export default, do no need to destructure. But can only export 1 thing <br />- name do not need to match<br />`export default ["apple", "durian"]` | `import MyFruits from "./fileA"`                             |



##### Pure Functions

1. no side effect
2. no mutations
3. with an input = will always get back the consistent output

------



##### Ways to create a functional component

```react
//Method 1 - when using props
function Something(props){
    return(
        <div>{props.name}</div>
    )
}

//Methond 2 - using destructuring
function SomethingElse({name}){
    return(
    	<div>{name}</div>
    )
}

function App(){
    return(
    	<div>
            <Something name={"John"}/>
        </div>
    )
}
```



