10th Oct 2019

## Mongoose & Authentication

- Documents and subdocuments
  - if your subdocument is a document array it has .id() to search a document given its _id()
  - useful for a person who has an address, and in that address has a country (that is fixed) 
  - mini collection that is inside the parent collection = an array within an array 
- version key 
  - `__v` is set to 0 upon first creation (meant for mongoose to keep tracks of the version)
  - it increments only whenever you do a `.save()` operation on the document 
  - however when `update()` or `findOneAndUpdate()` it will not increment
- Validation
  - defined with Schema type
  - Mongoose validates automatically only on `.save()`
  - does not validate automatically on `.update()`
  - To validate `.update()`, must set `{runValidators:true}`
  - Mongoose does not validate if a value is unique. It leaves it to MongoDB - because MongoDB is the one indexing, thus will be the one who will know if there is a duplicate in the entry
- Middleware
  - similar to Express
  - plugin architecture that allows to add in more and more functions that you can call using `require` 



### Authentication

- storing passwords
- staying authenticated

###### Hash algorithm 

- one way function

- converts the passwords to another string

- standard algorithms, easy to hack 

- rainbow tables - precomputed table for reversing cryptographic hash functions, for cracking password hashes

  

###### Hash + SALT

- same additional characters (like a 2nd password) added to the password, so that make it slightly more difficult to hack the hashing algorithm



###### Hash + Unique SALT

###### BCRYPT

- generates a unique salt for each password that is generated on the fly
- the unique salt is stored in the hash itself
- HASH - converts plain text to a hashed : string
- COMPARE -  compares the plain text and the hashed : boolean 

`npm i bcryptjs`

https://www.npmjs.com/package/bcryptjs

```js
// in the routes file
router.post("/new", async (req, res, next) => {
  try {
    const owner = new Owner(req.body);

    const bcrypt = require("bcryptjs");
    const rounds = 10;
    const hash = await bcrypt.hash(owner.password, rounds);
    owner.password = hash;

    
    await Owner.init();
    const newOwner = await owner.save();
    res.send(newOwner);
  } catch (err) {
    if (err.name === "ValidationError") {
      err.status = 400;
    }
    next(err);
  }
});

//however, we can presave the hash as a function - Mongoose middleware
ownerSchema.pre("save", async function(next) {
  const rounds = 10;
  this.password = await bcrypt.hash(this.password, rounds);
  next();
});
```

To authenticate/ compare the password during login

```js
router.post("/login", async (req, res, next) => {
  try {
    const { userName, password } = req.body;
    const owner = await Owner.findOne({ userName });

    const bcrypt = require("bcryptjs");
    const result = await bcrypt.compare(password, owner.password);
    if (!result) {
      throw new Error("Login failed");
    }
    res.send(owner);
  } catch (err) {
    if (err.message === "Login failed") {
      err.status = 400;
    }
    next(err);
  }
});
```

##### Testing the hash

- `not.toBe()`
- mock the bcrypt hash function



