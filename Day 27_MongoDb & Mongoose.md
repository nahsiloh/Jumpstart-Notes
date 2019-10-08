8th Oct 2019

## MongoDB

- set the default dbpath - in git bash

  `mongod --dbpath ~/data/db`

- Mongo is the server, there are many ways to speak to the server 

  - Mongo shell is a user interface that talks to the mongodb server through an API
  - Azure Cosmos - vs Code
  - Compass
  - Express



##### Mongo Shell

- start mongo shell - `mongo`

- show database - `show dbs`

- to create a test db`use test`

  - however, the db will not show until a new collection is created

- create  a collection - `db.myFirstCollection.insertOne({name: 'Bob'})`

- show collection - `show collections`

- `db.myFirstCollection.find()`

  returns: `{ "_id" : ObjectId("5d9bf7d9b1fdde669c75d6cc"), "name" : "bob" }`

  `book._id` is used to return this ObjectId

https://docs.mongodb.com/manual/tutorial/update-documents/index.html



- there is no schema. Can add multiple of the same items, and different formats



##### Azure Cosmos

- in VS code



## Mongoose

https://mongoosejs.com/docs/index.html

`npm install mongoose`

##### The files can be separated like that:

- ##### Connecting to the database

  ```js
  const mongoose = require("mongoose");
  const dbName = "test";
  
  mongoose.connect(`mongodb://localhost/${dbName}`, {
    useNewUrlParser: true,
    useUnifiedTopology: true
  });
  
  const db = mongoose.connection;
  db.on("error", console.error.bind(console, "connection error:"));
  db.once("open", function() {
    console.log("Connected to MongoDB server");
  });
  ```

  #####  

- ##### Defining the Schema and model

  ```js
  //creating a schema
  const kittySchema = new mongoose.Schema({
    name: String
  });
  
  //creating a model
  //this is the collection
  const Kitten = mongoose.model("Kitten", kittySchema);
  ```

  

- ##### Creating new instance of the model/ document

  ```js
  app.post("/kittens/new", (req, res) => {
    const fluffy = new Kitten({ name: "Fluffy" });
    fluffy.save((err, kittens) => {
      if (err) {
        console.error(err);
        next(err);
      }
      console.log(kittens);
      res.send("kitten created");
    });
  });
  ```

  

- ##### Promises vs Async Await

  ```js
  //callback method
  app.get("/kittens", (req, res) => {
    Kitten.find((err, kittens, next) => {
      if (err) {
        console.error(err);
        next(err);
      }
      res.send(kittens);
    });
  });
  
  
  //promise
  app.get("/kittens", (req, res) => {
    Kitten.find()
      .then(kittens => res.send(kittens))
      .catch(err => next(err));
  });
  
  //async & await
  app.get("/kittens", async (req, res, next) => {
    try {
      const kittens = await Kitten.find();
      res.send(kittens);
    } catch (err) {
      next(err);
    }
  });
  ```

  

##### Schema Types

https://mongoosejs.com/docs/schematypes.html

###### string

- enum = Array of valid words that we can use 

```js
//essentially printing out "North"
const direction = DIR.N

// this is the javascript enum:
DIR = {
    N: "North"
    S: "South"
    E: "East"
    W: "West"
}
```



- creating unique text index

```js
router.post("/new", async (req, res, next) => {
  const newKitten = req.body;
  const addKitten = new Kitten(newKitten);

  try {
    //indexes the database
    await Kitten.init();
    //saves the name in the database
    //this throws the error when the name is not unique
    await addKitten.save();
    res.send(addKitten);
  } catch (err) {
    if (err.name === "ValidationError") {
      err.status = 400;
    }
    next(err);
  }
});
```



