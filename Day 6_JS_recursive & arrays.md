9th sept 2019

## Javascript - Recursive function & Arrays

### Convert value to a true and false value

- ! = invert and return as boolean
- !! = invert and invert = used to return a boolean value

### Recursive function

- call the same function inside another function 

```js
//palindrome
function isPalindrome(word){
    if(word.length <= 1){
        return true;
	}

	const firstChar = word.substring(0,1);
	const lastChar = word.substring(str.length-1);
	if (firstChar !== lastChar){
    	return false;
	}
    
    const middle = word.substring(1, str.length-1);
    return isPalindrome(middle);
}

console.log("anna should return true", isPalindrome("anna"))
console.log("tom should return false", isPalindrome("tom"))
```



### Array

`array = []`

- Arrays are non discriminate - can hold numbers, strings, objects and functions

- #### forEach()

```js
const array = [1, "2", "{num = 3}", ()=>{return 4}]

//to print everything in the array
//for(  ; exit condition; incremental condition)
for(let i = 0; i<array.length; i++){
    const curItem = array[i]
}

//using iterables to run through the array
for (let i of array){
    console.log(i)
}

//using forEach to iterate
//the forEach will not work when it is in a function therefore, will use the 1st method instead = `for(let i = 0; i<array.length; i++)`
array.forEach((item, i, array)=>{
    console.log(array[i] === item);
    console.log(item)
})
```



- the forEach will not work when it is in a function 

```js
function b(){
    for (let i of array){
        return true
    }
    console.log("end of b")
}
// true

function a(){
    //this is an inner function
    array.forEach((item, i, array)=>{
        return true
    })
    console.log("end of a")
}
//"end of a"

//when there is an inner function, this will not exit out of the outer function. Thus the result of the inner function will not be passed out of the outer function
```



```js
const object ={
    name:"asdf",
    age: 123,
}

for (let i in object){
    console.(i)
}
```



- #### map()  ***(especially impt for React)

  - return a new array, with the same length as the original array
  - used to change structure of the data inside the original array
  - content of new array depends on the returning value of the function that will be passed in 

```js
const markedPokemons = data.map(item =>({
    id = item.id
    name = item.name.english
}))


// same as
const markedPokemons = data.map(item =>{
    return{
        id = item.id
        name = item.name.english
    }
})
```

 

- #### filter()

  - usually returns a smaller array
  
  - return the subset of an array if the condition is true

```js
const attackHigherThan70 = data.filter(item =>{
    if (item.base.attack >70){
        return True
    }
    return False
})
```



- #### some()

  - check if an array contains some-type of a same value, for at least one item
  - returns a boolean value

```js
const types = ["ice", "stone", "fire"]
console.log(types.some(item => item==="fire"))
```



- #### reduce()

  1. sum data within dataset

  2. push values into a new array

     

     https://sidburn.github.io/blog/2017/03/19/understanding-fold

  - combining multiple values into a single value
  - accumulator = counter/ where to start from the list. i.e [i]
  - currentValue = total
  - reduce always need to return acc (accumulator)

```js
const addAllAttackOfPsychicTypes = data.reduce((acc, cur)=>{
    return ++acc;
})

const numbers = [1, 2, 5, 8]
let total = 0
numbers.forEach(number => (total = number + total))
console.log(number)

//Same As
const totalnumbers = numbers.reduce((acc,cur)=>{
    return acc + cur
},0)
// 0 = is to set the original value as 0, otherwise, will take in the first value of the list 
```



- #### every()

  - to ensure that every item meets a certain condition

    

- #### method chaining

  - place filter first, so that the filter will reduce the list first 

```js
function squareSum(numbers){
    const squaredNum = numbers.map(num => num **2)
    const totalNum = squaredNum.reduce((acc,cur)=>{return acc+cur},0)
    return totalNum
}

//method chaining
//modularises the function so that it is easier to manipulate
function squareSum(numbers){
    return numbers
    	.filter(num => num%2 ===0)
        .map(num=>num**2)
        .reduce((acc,cur)=>{return acc+cur},0)
}
```



- #### sort()

  - mutates the original array **
  - need to pass in comparison function that returns a positive or negative number; as it sorts by Unicode by default
- a positive number will return in ascending order, and a negative number will return descending order
  
  ```js
  const numbersToSort = [1, 10000, 90, 75, 56]
  
  // when a-b, arranged in ascending order
  const sortedNumber = numbersToSort.sort((a,b) => a-b)
  
  // when b-a, arranged in descending order
  const sortedNumber = numbersToSort.sort((a,b) => b-a)
  ```
  
  ```js
  //to sort by count
  const countArray = [{count:2}, {count:100}, {count:75}, {count:56}]
  const sortArray = countArray.sort((a,b) => a.count- b.count)
  ```
  
  ```js
  //to sort by length
  const array = [[1,2], [1,2,3,4], [1], [1,2,3,4,5]]
  const sortArray = array.sort((a,b) => a.length- b.length)
  ```
  
  ```js
  //sort to ["a", "b", "A", "B"]
  const array = ['b', 'a', 'A', 'B']
  const isCapLetter = (char)=> char >= 'A' && char <= 'Z'
  const sortArray = array.sort((a,b)=>{
      if 
      
  })
  
  
  
  ```
  
  

- #### Changing data in the array

  - #### Add items in array

    - ##### push()

      - adds something into an array, will always append data to the end of an array

    - ##### unshift()

      - pushes data to the front when added 
  
    #### Remove items in array
    
    - ##### pop()
    
      - removes the last item in an array
    
    - ##### shift()
    
      - removes the first item in an array
  
```js
  const arrays = []
arrays.push(1) //[1]
  arrays.push(2) //[1, 2]
arrays.unshift(0) //[0, 1, 2]
  arrays.unshit(-1) //[-1, 0, 1, 2]

  const lastItem = arrays.pop() //2 [-1, 0, 1]
const firstItem = arrays.shift() //-1 [0, 1]
```

  

- #### Destructuring arrays

  - this does not change the array

  ```js
  const destructureArray = [1, 2, 3, 4, 5]
  let [firstitem, ...res] = destructureArray
  console.log(firstitem)
  // 1
  console.log(...res)
  //[2, 3, 4, 5]
  console.log(destructureArray)
  //[1, 2, 3, 4, 5]
  ```

  - can clone an array with the destructuring method

  ```js
  const addClone = [...destructureArray]
  ```

  - when an object is in the original Array, and when you change the value of the object inside the clone, the original array object will also be affected. 
  - numbers and strings = are stored by values
  - objects and arrays = are stored by memory address of the object or the array

  ```js
  const originalArray = [1, 2, [], {}]
  const cloneArray = [...originalArray]
  
  cloneArray[0] = 999
  cloneArray[2][] = "new item"
  cloneArray[cloneArray.length-1].name = "John"
  
  console.log(originalArray)
  //[1, 2, ["new item"], {name: "John"}]
  
  console.log(cloneArray)
  //[999, 2, ["new item"], {name: "John"}]
  
  ```

  ##### accessing the value of individual item in the object 
  
  ```js
  object1 = { name : "john"}
  
  //this is a destructuring step
  const {name} = object1
  
  console.log(name)
  // will return "john"
  ```
  
  

- #### To swap values in an array

  ```js
  const temp = array[i]
  array[i] = array[i-1];
  array[i-1] = temp
  ```

  