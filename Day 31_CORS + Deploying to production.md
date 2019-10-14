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
- CORS

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



###### Connecting the FrontEnd and the Backend

