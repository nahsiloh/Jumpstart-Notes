11th Oct 2019

## Json Web Tokens

1. Creating a protected route that is only accessible if a user is logged in 
   - failed login = status code unauthorized 401
   - login successful = status code 200

2.  Grant access if logged in 

   

##### Sending information back to client

- send json using `res.send()`
- send header using `res.set()`



##### Types of authentication tokens

1. ###### Cookies

   - Send a cookie to the header once the user is logged it. The cookie will be set in the header for all the routes

   - only 1 cookie

      

2. ###### Sessions

   - different code for each user which is stored in a table

   ```js
   code = {
       sessionId1: "apple"
       sessionId2: "banana"
   }
   ```

   

3. ###### Self contained token - JWT

   https://jwt.io/
   
   https://medium.com/swlh/a-practical-guide-for-jwt-authentication-using-nodejs-and-express-d48369e7e6d4
   
   
   
   - unique for each logged in user and a device
   
   - ###### base64URL
   
     - an algorithm that converts binary data (or text data) into a format that can be carried in HTTP request URL or headers
   
   - does not encrypt data. Just uses **base64 URL** to encode/decode 
   
     - in console, can use 
   
       `atob("eyJuYW1lIjoiQWFsaXlhaCBHb3lldHRlIiwiaWF0IjoxNTcwNzg3ODExfQ")`
   
       `"{"name":"Aaliyah Goyette","iat":1570787811}"`
   
       to retrieve the encoded web token
   
       https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/atob
   
       
   

<img src="https://miro.medium.com/max/2921/1*4W8JT5yod3lBvYSL6uN1DQ.png" alt="img" style="zoom: 30%;" />

- JWT = header.payload.signature
- **Header** =  contains the algorithm to encrypt it
- **Payload** = any information other that passwords
  - ID, name, user agent, logged in time and date(so that the token may be set to expire accordingly)
  - for example in e-commerce site, can set the currency preference in the payload
- **Signature verification** = includes a secret key, but should not be store in the code, but in the .env file

- ##### Submitting JWT tokens to the browser

  - could be done in multiple ways

  1. ###### Authorization Bearer Token
  
   - using HTTP request header, using `Authorization: Bearer <token>`
     - not automatic. require to manually insert the authorization bearer tokens
     
  2. ###### In the URL
  
     - like in the google map API 
  
  

#### Install Jsonwebtoken library

https://www.npmjs.com/package/jsonwebtoken

`npm install jsonwebtoken`

- `jwt.sign(payload, secretOrPrivateKey,[options,callback])`

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

    const token = jwt.sign({ name: owner.userName }, "abcde");
    res.cookie("token", token);

    res.send(owner);
  } catch (err) {
    if (err.message === "Login failed") {
      err.status = 400;
    }
    next(err);
  }
});
```



- `jwt.verify(token, secretOrPrivateKey, [options, callback])`

```js
router.get("/secret", async (req, res, next) => {
  try {
    if (!req.cookies.token) {
      throw new Error("Go Away!");
    }
    const user = jwt.verify(req.cookies.token, "abcde");
    res.send(`Hello ${user.name}`);
  } catch (err) {
    err.status(401);
    next();
  }
});
```



- JWT does not address an attacker hijacking your JWT token
- To prevent this use `httpOnly`



##### Authentication vs Authorizaton

Authentication - identify a user

Authorization - access rights, allowed to perform an action