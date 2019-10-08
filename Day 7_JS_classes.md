10th sept 2019

## Javascript - Classes

### Classes

```js
class Truck{
    constructor(name){
        this.name = name;
    }
    getName(){
        return this.name
    }
    //this is a static method
    static isColour(colour){
        console.log("Truck is", colour)
    }   
}
```

- ##### Static functions

  - Create a function that calculate values that are not related to a specific instance of the class
  - Do not need to create an instance of the class



- ##### Getters and Setters

  - Getter = changes the way the value is accessed = must always have a return statement
  - Setter = changes the value 

```

```

- ##### Extends

```js
class Vehicles{
    constructor(colour){
        this.colour = colour
    }
}

class Bicycle extends Vehicles{
    constructor(wheels, colour){
        super(green);
        // this is from the vehicles constructor 
        this.wheels = wheels; 
    }
}
```



##### rounding numbers

```js
//.toFixed will put the number into a string 
//Number() converts it back
Number((0.1+0.2).toFixed(2))
```



### Strings

- string manipulation
- ("") = this is called a tokenizer

```js
const string = "qwertyuiop";

// split string to array
const stringArray = string.split("")

// join array back to string
const newString = stringArray.join(",")

//to .toUpperCase & .toLowerCase
```



### Error

```js
function divide(dividend, divisor) {
    if(typeof dividend !== "number"){
        throw new Error("new error message here") 
    }
}

//try to check if an item has error
try {
    divide(4, "2")
    console.log("will not run due to error")
} catch (e){
    // to print the error message
    console.log(e.message)
} finally {
    console.log("Finally will run regardless of any error above")
}

```



