11 sept 2019

## Module

- Package code in file so that other code does not affect your code



##### Common JS vs Browser module

- difference browser has different JS engine eg. Chrome uses V8

- JIT= just in time 
- JIT compiler coverts the code into binary



```js
const getCircleArea = require('./circle.js')


// this is in the ./circle.js file
// 2 methods of creating a module.exports
//Method 1
module.exports = {
    getArea : (radius) => Math.PI * radius * radius,
}

//Method 2
module.exports.getArea = (radius) => Math.PI * radius * radius,
    

//the "require" statement will look for the corresponding "module.exports" and return that value 
const getCircleArea = {
    getArea : (radius) => Math.PI * radius * radius,
}

// using object destructuring to get the item in the object
const {getArea} = {
    getArea : (radius) => Math.PI * radius * radius,
}

// therefore can use: 
const {getArea} = require('./circle.js')
```

- if the class only contains static methods, better to put it in an object to call rather than in a class

|                                                              | in the `circle.js`file            |
| ------------------------------------------------------------ | --------------------------------- |
| This returns the class<br />`const Circle = require('./circle.js')` | `module.exports = class Circle{}` |
| This returns the object, usually used on a constant file<br />`const Circle = require('./circle.js')` | `module.exports = {getArea: ...}` |
| This returns the function in an object<br />`const{getArea} = require('./circle.js')` | `module.exports = {getArea: ...}` |
| This returns a function<br />`const{getArea} = require('./circle.js')` | `module.exports.getArea = {...}`  |

