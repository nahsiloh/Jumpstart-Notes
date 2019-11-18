## React Redux

`npm install redux react-redux`

- redux is the state management package
- react-redux connects react and redux together



1. Store

   - globalized state

   - can be accessed by all the components

   - `import {createStore} from "redux" `

     

2. Action

   - describes what you want to do

   - returns and object

     

3. Reducer

   - checks the action and see what needs to be done from the dispatch

   - executes the action to manipulate the data in the store



4. Dispatch 

   - send the action to the reducer

     

```react
import { createStore } from "redux";

//Store

//Action
const increment = () => {
  return {
    type: "INCREMENT"
  };
};

const decrement = () => {
  return {
    type: "DECREMENT"
  };
};

//Reducer
const counter = (state = 0, action) => {
  switch (action.type) {
    case "INCREMENT":
      return state + 1;
    case "DECREMENT":
      return state - 1;
  }
};

let store = createStore(counter);

//Display in console
store.subscribe(() => console.log(store.getState()));

//Dispatch action
store.dispatch(increment());
store.dispatch(decrement());
store.dispatch(decrement());
```



Chrome extension for redux

https://github.com/zalmoxisus/redux-devtools-extension

```react
 const store = createStore(
   reducer,
   window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()
 );
```

