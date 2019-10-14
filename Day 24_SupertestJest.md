3rd Oct 2019

## Supertest / Jest 

##### Install Supertest and Jest	

`npm install supertest --save-dev`

``npm install jest --save-dev`

- require to add in package.json `scripts`

  ```js
  "test":"jest"
  "test:watch": "jest --watch"
  ```



##### Mocking Modules

- the database is mocked when we are testing the routes 

- the database will always be changing. So when we write our tests, it should be testing the functionality of getting a response, rather than to check the data in the database
- thus, we should mock the data in the database, regardless of whether the database is changing 

```js
const request = require("supertest");
const app = require("../app");
const book = require("../models/Book");

jest.mock("../models/Book");

const mockData = [
  { id: 1, title: "Pattern Language", author: "Alan" },
  { id: 2, title: "Javascript 101", author: "Ben" },
  { id: 3, title: "Coding 101", author: "Chris" }
];

describe("/books", () => {
  it("[GET]/books returns all books", () => {
    book.getAllBooks.mockReturnValueOnce(mockData)
    return request(app)
      .get("/books")
      .expect(200)
      //should place the entire list of returns inside the expect statement rather than expect(mockData)
      .expect([
          { id: 1, title: "Pattern Language", author: "Alan" },
          { id: 2, title: "Javascript 101", author: "Ben" },
          { id: 3, title: "Coding 101", author: "Chris" }
    ])
  })
  
  
  it("[POST] /books returns correct message", () => {
    const newBook = { id: 6, title: "Talking to strangers", author: "Faith" };

    return request(app)
      .post("/books/new")
      .send(newBook)
      .expect(200)
      .expect({ id: 6, title: "Talking to strangers", author: "Faith" })
      //the 1st expect is from Supertest, 2nd expect is from Jest
      .expect(() => {
        expect(book.addBook).toHaveBeenCalledTimes(1);
      });
  });
}
```



##### Supertest vs Superagent

```js
//superagent
request(App)
	//superagent
	.get("/books")
	//superagent
	.query({})
	//supertest - provides the assertions
	.expect()
```

