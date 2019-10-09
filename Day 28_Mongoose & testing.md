9th Oct 2019

## Mongoose

#### Some Mongoose functions

##### Model.create() vs Model.prototype.save()

- `create()`allows for saving of more than one document to the database
- essentially ``create()` is a for loop created to allow for an array of objects that are passed in to be saved one by one
- but essentially they are the same. `Model.create()` automatically triggers `save()`



##### Model.bulkWrite()

- Sends multiple operations to the MongoDB server in one command. This is faster because with `bulkWrite()` there is only one round trip to MongoDB.

  This function does **not** trigger any middleware, not `save()` nor `update()`. If you need to trigger `save()` middleware for every document use [`create()`](http://mongoosejs.com/docs/api.html#model_Model.create) instead.

- typically used for seeding the data



##### Model.init()

- This function is responsible for building indexes, unless `autoIndex` is turned off.

  Mongoose calls this function automatically when a model is created using so you don't need to call it. This function is also **idempotent**, so you may call it to get back a promise that will resolve when your indexes are finished building.

- idempotent - the result remains the same no matter how many times the operations are run



##### Virtuals

https://mongoosejs.com/docs/guide.html#virtuals

- document properties that you can get and set but that **do not get persisted to MongoDB**. 

- `._id` => `ObjectId()`
- `.id` => `String(virtual)`

```js
//inside the model file
const ownerSchema = new mongoose.Schema({
  firstName: String,
  lastName: String,
  salutation: { type: String, enum: ["Mr", "Mrs", "Ms", "Mdm", "Miss"] }
});

//creating a virtual
//for properties that do not require to be saved in the database, like for instance the full name
ownerSchema.virtual("fullName").get(function() {
  return `${this.salutation} ${this.firstName} ${this.lastName}`;
});
```



#### CRUD Operations

- Create
  - `save()`
  - eg. `const newBook = new Book(req.body)` then `await newBook.save()`

- Read
  - `.find()`
  - `.findOne()`
- Update
  - `findOneAndUpdate(condition, update)`
- Delete
  - `findOneAndDelete()`



#### Environments

- For windows, require to install this package to use NODE_ENV to set the node environment, otherwise, will show error NODE_ENV not found

https://www.npmjs.com/package/cross-env

`npm install --save-dev cross-env`

```json
"scripts": {
    "start:dev": "cross-env NODE_ENV=watermelon nodemon index.js",
}
```

- Express allows to use `app.get("env")` but some other APIs may not support this, thus will need to set using `process.env.NODE_ENV`



## Testing

##### Test Environment

- Jest will automatically change the environment to the test environment

//errror will occur 

- Mongoose: looks like you're trying to test a Mongoose app with Jest's default jsdom test environment. Please make sure you read Mongoose's docs on configuring Jest to test Node.js apps: http://mongoosejs.com/docs/jest.html

```js
//create another file jest.config.js
module.exports = {
  testEnvironment: "node"
};
```



##### Unit tests

- the test does not hit the database. Just testing the routes. Therefore mock data is created to test the routes
- low-level test
- Schema does not get tested



##### Integration tests

- Will require to hit the database. However, we do not want to pollute the actual database.
- Thus, an in-memory database (light-weight, using RAM) is created that will be deleted once reset
- To access the in-memory database, will need to create a logic to switch the database during testing environment
  1. connect to in-memory DB
  2. seed DB 



##### Create the in-memory database

https://github.com/nodkz/mongodb-memory-server

