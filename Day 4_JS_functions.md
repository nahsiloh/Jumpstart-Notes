5th sept 2019

## Javascript -Functions

- Syntax 101

  <img src="C:\Users\lisha\AppData\Roaming\Typora\typora-user-images\1568014650568.png" alt="1568014650568" style="zoom:80%;" />

- Array is an object

``` javascript
console.log(typeof[]) 
//object

console.log(Array.isArray([]))
// array
```

- Syntax

```js
for (i=0; i<10; i++){
	console.log(i)
}
//prints 1-10
```

- #### Scope
  
  <img src="C:\Users\lisha\AppData\Roaming\Typora\typora-user-images\1567759383729.png" alt="1567759383729" style="zoom:75%;" />
  
- either function scope (within a function) or block scope (within a block - eg. if, while, for etc. - items in {})
  
- #### Difference between const, let and var
  
  ![1567759203826](C:\Users\lisha\AppData\Roaming\Typora\typora-user-images\1567759203826.png)
  
- difference in scope 
  
  - when const, let and var are in a function/ block, will be able to access any const, let and var outside.
  
  - ###### const and let 
  
    - block scope = values that can only be accessed within a block
    - function scope
  
  - ###### var
  
    - function scope = values that can be accessed when inside a block
  
     -- try not to use (as they can be accessed globally)
  
    
  
- ### conversion of types

  - `number("123")`= to convert number to string

  ##### **When calling `isNaN`, should always call it with `isNaN(Number("string"))`

  - `isNaN(Number("123"))` 

    This is false

    `.isNaN(Number("abc"))`

    This is true

    = to check if its a number

    

- And (&&) will always occur before Or (||)

  

- Ternary Conditional statements

  - `const result = true ? 1 : 2`

    condition ? doSomethingIfTrue() : doSomethingIfFalse()

    

- #### Boolean Values (True, False)

  ```js
  !!0 => false
  !!1 => true
  !!0.1 => true
  !!-0.1 => true
  !!"" => false
  !!"abc" =>true
  !!{} => true
  !![] => true
  !!null => false
  !!undefined => false
  ```



- #### Operators

  - `>  <  >=  <=`
    - typically used for numbers
    - if  used for characters, will be used to compare the unicode of the alphabets

  ```js
  "a".charCodeAt()//97
  "z".charCodeAt()//122
  "A".charCodeAt()//65
  "Z".charCodeAt()//90
  ```

  - `==  !=  ===  !==`

  ```js
  1 == 1 //true
  1 == "1" //true
  // the + in front of the string "1" converts it to a number
  1 == +"1" //true
  ```

  ```js
  1 === 1 //true
  1 === "1" //false
  
  1 !== 1 //false
  1 !== "1" //true
  ```

  

- #### Null & Undefined

  - undefined means the variable/ function has not be set before
  - null means that the variable/ function is empty

```js
let apple; //undefined

//if you want to unset a variable, should set:
apple = null

// when a variable returns null means that this variable has been set before. Whereas undefined means variable has not be assigned before

const fruit; //throw error
//therefore const forces a value to be set 
```



- Setting default values in a function

  ```javascript
  // will return default in console
  function a(something="default"){
  	something = something;
  	console.log(something);
  }
  
  // this will not print as false && will cause an early exit
  false && a("Print A")
  // same representation
  if (false){
      a("Print A")
  }
  
  // true && will run
  true && a("Print B")
  
  ```

  

- #### Functions

  ```javascript
  functionKeyWord functionName(Parameter, Parameter){
  	return Parameter*Parameter
  }
  
  functionName(Argument, Argument)
  ```

  

  - Auto creates a list if more arguments are given

  ```javascript
  function sumValues(first, ...rest){
  	console.log(first)
  	console.log(rest)
  }
  
  sumValues(1, 2, 3, 4, 5, 6)
  
  // console will return 
  //1
  //[2, 3, 4, 5, 6]
  ```

  

  - To immediately print a function

  ```js
  //IIFE, Immediate Invoke Function Expression
  //So that the script will automatically print
  //var in IIFE 
  
  (funtion printHello(){
  	console.log("hello")
  })();
  ```

  

  - Function as a first class object 

  ```js
  //function as a variable
  //in Javascript all functions are automatically moved to the top = called hoisting (thus all the functions will run first)
  //good for functions that are not used as frequently (faster speed when loading - may be minimal)
  const getPrice = function(price, discount){
      return price * discount;
  };
  console.log(getPrice(100,0.1));
  
  //method within object
  const calculator ={
      add: function(a,b) {
          return a + b;
      },
      subtract: function(a,b) {
          return a - b;
      }
  };
  console.log(calculator.add(10,20))
  
  //arrays can contain functions
  const array = [
      function() {
          console.log("do something in array")
      },
      "something"
  ]
  array[0]()
  
  //functions can return functions
  function sayHelloFactory(name){
      return function(){
          console.log("hello ", name)
      }
  }
  
  const sayHellotoJohn = sayHelloFactory("John")
  const sayHellotoMary = sayHelloFactory("Mary")
  
  sayHellotoJohn()
  sayHellotoMary()
  ```

  
  
  ###### - In objects if you want a reference to the current object (aka "this") use a normal function
  
  ```js
  const obj = {
    name:"John",
    printName:function(){
      console.log(`normal ${this.name}`);
    },
    printNameArrow: () => {
      console.log(`arrow ${this.name}`);
  }
  }
  
  obj.printName(); //normal John
  obj.printNameArrow(); //arrow undefined
  ```
  
  
  
  - #### Arrow functions
  
  - arg => function(arg)
  
  ```javascript
  //Arrow functions
  const multiply = function (a,b){
      return a*b;
  }
  
  // same as
  const multiply = (a,b) => {
      return a*b;
  }
  
  //same as
  const multiply = (a,b) => a*b
  
  ```
  
  ```js
  () => 1 === 1 //true
  () => {1 === 1} //undefined
  () => {
      return 1 === 1
  } //true
  
  
  () => {} //undefined
  () => ({}) //{}
  () => {
      return {}
  } //{}
  ```

   

  - #### Lexical scope of arrow functions
  
  ```js
  //functions are executed using the scope chain that was in effect when they were defined
  //this is used to retrieve something within an object (like dictionary)
  const object ={
      number: 976769,
      getDate: function(){
        console.log(this.number)
      }
  }
  //this will print out the number within the object 
console.log(object.getDate(), object.getThis()===object)
  ```
  
  ```js
  //where the function is being declared
  
  this.hello = "hello from where the functions are define";
  
  function normalFn() {
    return this.hello;
  }
  
  const arrowFn = () => {
    return this.hello;
  };
  
  //another one in the function wrapper 
  function wrapper() {
    this.hello = "hello from wrapper";
    console.log("normal function", normalFn());
      //normalfn called within the same wrapper 
  
    console.log("arrow function", arrowFn());
  	//arrowfn called where its being declared
      
    assert(normalFn() === "hello from wrapper", "from wrapper");
  arrowFn(arrowFn() === "hello from out of wrapper", "from out of wrapper");
  }
  
  //thus arrowfn is preferred
  
wrapper();
  ```
  
  

