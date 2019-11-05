14th Oct 2019

## CORS + Deploying to production

##### Deploy to production 

- Heroku 

  - will provide a port number

- Port number, Environment variables  

  - automate process that changes the port automatically depending on whether we are in development, test or production environments (min. 3 environments)

  - development - my own computer (local) 

  - test - environment to reliably create test 

  - production - actual code that the customer will use 

    

  ### CORS

  - browser protection mechanism - that checks the headers

  - rejects any subdomain

    eg. to access dbs.com server, app.dbs.com will be rejected

  - an issue due to the separating of the frontend and the backend. Thus the frontend no longer sends html but json data

  

  https://www.npmjs.com/package/cors

  `npm install cors`

  ```js
  //without using CORS API
  app.use((req, res, next) => {
    res.set("Access-Control-Allow-Origin", "http://localhost:3000");
    res.set("Access-Control-Allow-Headers", "content-type");
    res.set("Access-Control-Allow-Credentials", true);
    next();
  });
  
  
  //using the CORS API
  const corsOptions = {
    origin: "http://localhost:3000",
    credentials: true,
    allowedHeaders: "content-type"
  };
  ```

  - Preflight - HTTP method [OPTIONS]



https://www.npmjs.com/package/cors

`npm install cors`

----------------------------------

###### Creating a login and logout mechanism to clear the cookies when someone logs out 

```js
router.post("/logout", (req, res) => {
  res.clearCookie("token").send("You are now logged out!");
});
```



###### General route structures

​			`/login`

​			`/logout`

[GET]  `/owners/:name`- protected route

[GET]   `/owners`- unprotected route



- for PUT and DELETE routes, preflight will check if there are rights to carry out these requests



###### Connecting the FrontEnd and the Backend



----------------

### Axios

https://github.com/axios/axios

##### - axios.post(url[, data[, config]])

```js
Axios.get()
	URL, config
	URL, payload, config 

//needs to be added to allow for all the routes to be accessible with the cookie
{withCredentials: true}
```

------------------

#### Dotenv

https://www.npmjs.com/package/dotenv



----------------------



#### Deploying to Heroku

1. Store the secret key in the .env file

   `npm install dotenv`

   create `.env ` file and save the `SECRET_KEY`

   

2. change the DB URL

   - at lease 2 DB URL - localhost and real production URL



3. change port number



- need to add in the `.env` variables into heroku in settings config var

- during deployment will need to push to git first, then from there git will push to heroku

`heroku logs -t` = to check the errors or status of the production

#### Check in Insomnia

- create development and production mode `baseUrl` to toggle between the 2 modes 