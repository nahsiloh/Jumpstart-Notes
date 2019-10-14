1st Oct 2019

## Express

Express = is a wrapper around node HTTP server, to better define routes 

https://expressjs.com/en/starter/basic-routing.html



#### Steps

1. ###### Create the package.json file

   `npm init`

   

2. ###### Install express

   `npm install express`

   

3. ###### Install nodemon

   `npm install --save-dev nodemon`

   

4. ###### Change the scripts in `package.json` file

```js
"scripts": {
    "start": "node index.js",
    "start:dev": "nodemon index.js"
  },
```



5. ###### Importing items required in index.js file

```js
const express = require("express")
const app = express(); 
```



6. ###### start server

`npm run start:dev`



7. ###### Testing a route

- method 1: manual testing using insomnia

- method 2: Supertest - https://github.com/visionmedia/supertest

  

  - Supertest will simulate the requesting to the server like insomnia.
  - Thus the base file cannot contain `app.listen()` - otherwise Supertest will not be able to control the server - conflict with express
  -  Works with any test framework. 

  

8. ###### Install Supertest and Jest	

   `npm install supertest --save-dev``

   ``npm install jest --save-dev`

   - require to add in package.json `scripts`

     ```js
"test":"jest"
     "test:watch": "jest --watch"
     ```



###### 9. Express Functions	

- ###### Middleware 

  - are functions that **have** **access** to the [request object](https://expressjs.com/en/4x/api.html#req) (`req`), the [response object](https://expressjs.com/en/4x/api.html#res) (`res`), and the `next` function. 
  - always request before response, like how HTTP functions

  ```js
  const middleware = (req, res, next) => {
    console.log("hello");
    next();
  };
  
  app.use(middleware);
  ```

- ###### Next

  - is a function that will execute the next function

- ###### Request Params - to set the url as a variable (GET)

```js
router.get("/:id", (req, res) => {
  const id = Number(req.params.id);
  res.send(book.getBookById(id));
});
```

- ###### Request Body - to add an input (POST)

```js
app.use(express.json());

router.post("/new", (req, res) => {
  const newBook = req.body;
  book.addNewBook(newBook);
  res.send(newBook);
});
```

- ###### Request Query - to search

```js
router.get("/", (req, res) => {
  const { author, title } = req.query;
  if (author) {
    res.send(book.filterBooks("author", author));
  }
  if (title) {
    res.send(book.filterBooks("title", title));
  }
  res.send(book.getAllBooks());
});
```



#### Install eslint

//eslint for javascript

`npm install eslint --save-dev`

`$ (npm bin)/eslint --init`

//eslint jest

`npm install --save-dev eslint-plugin-jest`

- in eslintrc.json file

```js
{
  "env": {
    "commonjs": true,
    "es6": true,
    "node": true,
    "jest/globals": true
  },
  "plugins": ["jest"],

  "extends": "eslint:recommended",
  "globals": {
    "Atomics": "readonly",
    "SharedArrayBuffer": "readonly"
  },
  "parserOptions": {
    "ecmaVersion": 2018
  },
  "rules": {}
}
```

- add script in `package.json` file

```js
"test:all": "npm run lint && npm run test"
```



**Linter** : check for syntax errors (Eslint)

**Code Formatter** : style (Prettier)