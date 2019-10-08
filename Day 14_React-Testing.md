19 sept 2019

## React - Testing

##### Front end testing

- Enzyme (created by airbnb)

  - tries to manipulate states and props

- React Testing Library

  - tries to do interaction through the React DOM 
  - write unit test like how user is expected to use it 
  - can be used in integration and unit level 

  

#### Installing React Testing Library

https://testing-library.com/docs/react-testing-library/cheatsheet

```bash
npm install --save-dev @testing-library/react
npm install --save-dev @testing-library/jest-dom
```

- In App.test.js file

```react
import React from "react";
import { render, fireEvent } from "@testing-library/react";
import "@testing-library/jest-dom/extend-expect";
import <Your Component> from "<path to your component>";
```

- standard test syntax

```js
describe("App",()=>{
    it("should show 1 when +1 button clicked once", ()=>{
        //require to render the page everytime! thus this line is required
        const{getByText} = render(<App/>);
        const addOneButton = getByText("+1");
        fireEvent.click(addOneButton);
        expect(getByText("0")).toBeInTheDocument()
    })
})
```

##### Accessing Test Coverage

```json
// run in terminal
npx react-scripts test --coverage --watchAll=false

//in Json package "scripts" add:
"coverage": "react-scripts test --coverage --watchAll=false"
```

- statement
- branch - if else logic
- functions
- lines

```json
// to add in package.json
"jest": {
	"coveragePathIgnorePatterns": [
	"./src/serviceWorker.js",
	"./src/index.js"
	]
}
```



##### Input box

```react
<input
    type ={"text"}
    aria-label = "name-of-label"
    onChange = {event => {}}
    value = {someValue}
    />
```



##### Event Change/ Set state

```react
//this should use an arrow function. Otherwise, will need a bind. 

handleChange = event => {
    //the event.target.value is to target the value of the event. Thus nothing to do with the state
    this.setState(() => {
      return { list: event.target.value };
    });
  };
```



##### When there are multiple same elements from different components - need to have within

```react
import {render, fireEvent, within} from "@testing-library/react"

it("should be able to come back to home page from blog",()=>{
    const{getByText, getByTestId} = render(<App/>)
    const NavBar = getByTestId("nav-bar")
    fireEvent.click(within(NavBar).getByText("Blog"))
    fireEvent.click(getByTest("Home"))
    expect(getByTestId("home-page")).toBeInTheDocument()
})
```



##### Testing for Fetch elements

1. open API on browser
2. open inspector - network - XHR & fetch / All
3. click on the API and response = to copy all the text
4. create test-data folder, with test-data.js file, and paste into the file.

```react
//inside the test-data.js file

export default{
    //paste the data 
    Bulbasaur
}
```

```react
//inside the test file
import React from "react";
import ReactDOM from "react-dom";
import App from "./App";
import { render, wait } from "@testing-library/react";
import "@testing-library/jest-dom/extend-expect";
import pokemonTestData from "./testData/pokemonTestData";
import mockFetch from "./fetch-utils";

describe("Pokemon APp", () => {
  beforeEach(() => {});
  it("renders without crashing", () => {
    const div = document.createElement("div");
    ReactDOM.render(<App />, div);
    ReactDOM.unmountComponentAtNode(div);
  });

  it("should render pokemon cards", async () => {
    window.fetch = jest.fn().mockResolvedValueOnce({
      json: jest.fn().mockResolvedValue(pokemonTestData),
    });

    mockFetch.mockOnce(pokemonTestData);
    const { debug, getByText, getAllByTestId } = render(<App />);
    await wait(() => getByText("Bulbasaur"));
    expect(getByText("Bulbasaur")).toBeInTheDocument();
    expect(getAllByTestId("cardComponent")).toHaveLength(4);
  });
});
```



```react
const realFetch = window.fetch;

export const mock = data => {
  if (window.fetch === realFetch) {
    window.fetch = jest.fn();
  }
  window.fetch.mock({
    json: jest.fn().mockResolvedValue(data),
  });
};

export const mockOnce = data => {
  if (window.fetch === realFetch) {
    window.fetch = jest.fn();
  }
  window.fetch.mockResolvedValueOnce({
    json: jest.fn().mockResolvedValue(data),
  });
};

export const mockRestore = () => {
  if (window.fetch !== realFetch) {
    window.fetch.mockRestore();
  }
};

export default {
  mock,
  mockOnce,
  mockRestore,
};
```

