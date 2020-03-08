30 sept 2019

## Backend Development

call a backend through an API 

API - interface to access a database/ server (eg. like a menu at a restaurant, you can order from, but you do not know how the kitchen is preparing the food)

designing APIs

load balancer - to distribute the users between the different servers 



##### What are you trying to solve?

- the problem of managing the load of the servers and distribute it efficiently 



IP address - public (typically for servers. Which will also have private networks) vs private networks (manage the internal networks)



##### internet web protocols

- ###### HTTP

  - `http://`  - always needs a request by the client for a response to be returned
    
  - eg. how do you create a live website? - will required polling, i.e `setInterval()`
    
  - stateless protocol - does not require the server to retain information

    - therefore, uses cookies. The browser stores the cookies from the website and returns back the cookies data to the website when a request is made 

    

- to change the structure of how information is passed, change the web protocol

- Web Socket - `ws://` - protocol that sets a life channel between the client and the database 

  - alternative for a live website



##### TCP/IP model

- ###### link layer 

  = the ethernet cable that connects one computer to another 

- ###### internet layer 

  = determines the IP address

- ###### transport layer 

  = TCP(transmission control protocol) - breaks down the data into small chunks (packet)

  - when data is sent, will check if the data is sent
  - used by HTTP

  = UDP- does not check the data that is sent

- ###### application layer 

  = HTTP



##### HTTP methods (CRUD)

API design - using HTTP methods to not create multiple links 



##### REST - representational state transfer

- API is a menu 
- which is a list of resources 



###### Datastore			HTTP Methods

Create		    -	   POST

Read			   -       GET

Update		   -       PUT/ PATCH

Delete		     -       DELETE



##### Questions

1. What are HTTP methods used for? Why are they necessary?



#### Creating a server

```js
//to change in the json file
"scripts": {
    "start": "node index.js",
    "start:dev": "nodemon index.js"
  },
```

`server.on()` - event listener

```js
const http = require("http");
const server = http.createServer();
const PORT = 3000;

server.on("request", (req, res) => {
  console.log("Connected to the server");
  res.end("Thank you");
});

server.listen(PORT, () => {
  console.log("Server is now listening to Port 3000");
});

```



`npm install --save-dev nodemon`

- tool that helps develop node.js based applications by automatically restarting the node application when file changes in the directory are detected.
- https://www.npmjs.com/package/nodemon



`npm run start:dev` 



install insomnia = allows you to see the post response