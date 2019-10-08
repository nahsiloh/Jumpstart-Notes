12 sept 2019

## Promises

- single thread vs multi thread
- multi-thread allows for multiple user possibilities
- Javascript runs on a single thread - runs one thing at a time 
- usually used to call APIs



- ##### Synchronous 

  - 2 scripts cannot run at the same time; they run one after another
  - when one piece of synchronous task is running, all the rest of the tasks are blocked

- ##### Asynchronous

  - asynchronous style is when all time-consuming tasks are executed in separate processes/ threads 
  - so that Javascript can juggle between multiple applications
  - if a tasks needs to take sometime(eg. reading a file from hard disk) the task should be executed asynchronously



##### Polling

- runs on a while loop. 
- while user does not terminate, will wait for the user response, then work on the user
- does not support multi-tasking to handle different users, will only move on to user 2 once the user 1 task is completed 
- eg. in a setTimeOut, polling will wait for set time out time to finish, will not be able to take the set time out time to do other things



##### Concurrency and parallelism 

- how Javascript handles multi- threading 

- Parallelism = where there is multiple threads (handles 2 or more users at the same time)

- Concurrency = how to handle parallelism in a single thread, which depends on the task 




##### Concurrency model and event loop

https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop



#### 3 results of a promise

1. ##### Resolve

2. ##### Reject

3. status unknown



- #### Basic Promise representation

```js
var promise1 = new Promise(function(resolve, reject) {
  setTimeout(function() {
    resolve('foo');
  }, 300);
})

//the .then takes in a function and is considered a method chaining
.then(function(value) {
  console.log(value);
  // expected output: "foo"
});

console.log(promise1);
// expected output: [object Promise]
```



- #### Representations of promises

```js
//Method 1
const success = () => console.log("success")

new Promise((resolve, reject)=>{
    resolve()
}).then(success, fail)// this resolves the success immediately

//Method 2
Promise.resolve().then(success,fail)

```



- #### Promise called with setTimeout()

```js
new Promise((resolve, reject) =>{
    setTimeout(() =>
              resolve(),
              ), 5 x 60 x 100); //this promise will be resolved after 5 mins
}).then(()=> doSomething(); // the `.then` is a method chaining
        );
```



```js
const success = sucess => console.log("success")
const failure = failure => console.log("failure")

//throw error with a failure function = will cause the failure function to execute but not the catch function
new Promise((resolve, reject)=>{
    throw new Error("Error");
    reject();
}).then(success, failure)
  .catch(error=>console.log(error.message)) //failure



//throw error with no resolve()/ reject() will return a fail
new Promise((resolve, reject)=>{
    throw new Error("Error");
}).then(success, failure)
  .catch(error =>{console.log(error.message)}) //failure


//place the catch before the .then to catch any errors first
new Promise((resolve, reject) => {
  throw new Error("My Personal Error");
}).catch(error => console.log(error.message))
  .then(() => {
      console.log("from resolve");
    },
    () => {
      console.log("from reject");
    }
  )


//using finally = which will run regardless = not typically used
new Promise((resolve, reject) => {
  throw new Error();
  resolve();
})
  .then(success, fail)
  .catch(e => console.log("error here"))
  .finally(() => console.log("happens no matter what")); // fail and "happens no matter what"



//when there is a promise, the promise moves to an event queue, and executes all the other code first before the promises
Promise.resolve("resolved value").then(success, failure)
console.log("end of file")
// end of file
// reolved value
```



#### Fetch

- fetch returns a promise

- browser has this function but not node.js 

- Therefore will need to npm install and require it 

  `const fetch = require("node-fetch")`

```js
fetch("https://....")
.then(response =>{
    ....
})

```



#### HTTP status code

200 = fetch data successfully 

201 = asking server to create data 

202 = server accepted data, but no reply required (not used very commonly)

204 = server accepted data, but no reply 

301 = someone changed domain = browser will redirect 

400 = data given to server is bad 

401 = no permission to do something 

403 = server knows who you are

404 = not found

422 = data is well-formed but weird errors occurring

500 = internal server error



- #### Async & Await

  - function will require async keyword to get the await keyword
  - Await = is a keyword to extract out the value of the promise 

```js
const promiseToGetMenu = Promise.resolve(["pizza", "coke"])

async function getMenu(){
    const menu = await promiseToGetMenu
    console.log(menu)
}

getMenu()
```

```js
const promiseToGetMeuni = new Promise((resolve, reject)=>{
    resolve(["pizza", "coke"])
}).then(menu=>console.log(menu))
```



- this shows the sequence of what is printed out first 

```js
const promiseToGetMenu = Promise.resolve(["pizza", "coke"])

//using async, you can put a promise within a function
async function getMenu(){
    console.log("2")
    const menu = await promiseToGetMenu;
    console.log("4")
    console.log(menu)
}

console.log("1")
getMenu()
console.log("3")
```

