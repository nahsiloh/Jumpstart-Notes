6th sept 2019

## Javascript - Constructors

#### Object Oriented Programming

- An Object is a `key : value` pair
- A constructor function: `function Pet(){}` allows for `new Pet()` to be created

```js
function Pet(name = "Bob", makesound){
    this.name = name
    this.makeSound = makeSound
}

// 1. creating a method that is unique to an instance created by the function
const frog = new Pet('Roger', ()=> console.log(`${name} says ribbit`))
const cat = new Pet('Grover', ()=> console.log(`${name} says meow`))

frog.makeSound() //creating a new function when creating the object
cat.makeSound()


// 2. if the function is shared within the constructor, using .prototype
Pet.prototype.isEating = function(){
    console.log(`${this.name} is eating `)
}
console.log("frog and cat are eating")

frog.isEating() //using prototype
cat.isEating()


//3. can invoke without creating an instance
Pet.move = function(){
    console.log("is moving")
}
Pet.move() //static method - help to manipulate or format a data, that does not belong to a particular instance that was created.

```



- instance method vs class method

  ```js
  //class method example
  Array.isArray()
  
  //instance method example
  //.prototype shows that this is an instance method
  Array.prototype.join()
  
  const arr = []
  arr.join()
  ```



- How to change the parent function by using .prototype

  - `.prototype` makes it a shared function
  
  ```js
  // this is an instance of the function Array
  //function Array(arr)
  const arr = [2, 1, 5]
  
  // this creates a method specifically for this instance of const arr
  arr.removeLastElement = function(){
      return arr.pop()
  }
  
  // this creates a method for the class of the arr which is Array
  Array.prototype.removeLastElement = function(){
      return arr.pop()
}
  ```
  



- #### Bind, Call, Apply

- Scoping of `this.` within functions

  - `this.` represents the instance of the object
  
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind
  
  - Bind = binds an instance to a function
  
    - returns a new function, thus will need to be called as a function
  
    - can be assigned as a variable 
  
  ```js
  function Pet(name){
      this.name = name
  }
  
  //method 1 is using arrow function => 
//arrow function cannot override bind
  
  //method 2 is to use this.
  // to add a .bind(this) so that the name is bounded 
  pet.prototype.getFood = function(){
      const wait = function(){
          console.log(`${this.name} has food`)
      }
      setTimeout(wait.bind(this), 1)
  }
  ```
  
  
  
  - Call function = when you want to pass in additional arguments when you bind
    - immediately invokes a function
    - cannot be assigned as a variable
  - Apply function = call function, except the arguments are taken in as arrays
    - used when using a res parameter
  
  ```js
  function () {
      this.name = "apple"
      function getPrice(price, qty) {
          return `${this.name} cost ${price * qty}`
      }
      
      function sumAll(...res){
      let total = 0;
      res.forEach(value => (total += value))
      return `{$this.name} cost ${total}`
  
  	}
      // getPrice.call({object}, price, qty)
      //i.e the additional arguments after are passed in for the inner function
      //parameters
      console.log(getPrice.call({name:"pear"}, 2, 3))
          
      console.log(sumAll.apply({name:"durian"}, [2, 3, 5, 8]))
  }
  ```
  
  
  
  ```js
  function(){
      const Animal = {
          says:function(owner){
              if (!owner){
                  return this.sound
              } else{
                  return `${owner}'s pet says ${this.sound}'`
              }
          return this.sound
      }
      }
  }
  
  function AnimalConstructor(sound){
      this.sound = sound
  }
  
  const cat = new AnimalConstructor("meow")
  const catSays = Animal.says.bind(cat)
  
  console.log(Animal.says.call(cat, "Alice"))
  ```



- #### Callbacks

  - call a function inside another function

  ```js
  function doSomething(cb){
      console("something");
      cb();
  }
  
  doSomething(() => console.log("Later"))
  ```

  #### Events

  - eg. setTimeout

  ```js
  const callback =() => console.log("one second have pass")
  setTimeout(callback, 1000)
  
  let counter=0;
  setInterval(() => console.log(++count + "second have pass"),1000)
  ```

  - eg. setInterval

  ```js
  const PrintOneSecond = () => {
    console.log("one second");
  };
  setInterval(PrintOneSecond, 1000);
  ```
  
  - when you pass in the function to be called later
  
  ```js
  setTimeOut(){
      doSomething, 1000
  }
  
  // function is called later = thats why doSomething is passed in without the function bracket. 
  // if called with bracket, then doSomething() will be invoked immediately
  ```
  
  

- #### Closure

  - is the combination of a function and the lexical environment within which that function was declared
  
  ```js
  function outer(name){
      return inner(){
          return name;
      }	
  }
  
  const innerJohn = outer('John')
  console.log(innerJohn())
  ```
  
  