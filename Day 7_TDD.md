10th Sept 2019

## KATA

### Test Driven Development (TDD)

### Jest

- install Jest library using the npm install method
- console command:  `npm install jest --save-dev`
- `npx jest --watchAll` to constantly run jest when code is edited

```bash
Method 1
// to run jest
 ./node_modules/.bin/jest filename.js
 
Method 2
//change the package.json file
change the "scripts":{
	"test":"jest"
}

//then call in console:
npm run test

Method 3
//npx == temporarily downloads a version of the programme if it is not downloaded before
//to call in console:
npx jest
```

- writing in `.test.js` file

```js
//to check if the test is running correctly = should return false 

describe("sum2Numbers", () => {
  it("should return the sum of 2 arguments", () => {
    expect(sum2Numbers(true)).toBeFalsy();
  });
});
```

- to link to the `.js` file

```js
const {sum2Numbers} = require("./sum2Numbers")

describe("sum2Numbers", () => {
  it("should return the sum of 2 arguments", () => {
    expect(sum2Numbers(1,2)).toBe(3);
  });
});
```



-------------------------------

##### Another Jest example

- writing in `.test.js` file

```js
//to check if the test is running correctly = should return false 

const { fizzBuzz } = require("./index.js");

describe("fizzBuzz", () => {
  it("should return 0 when pass in 0", () => {
    expect(fizzBuzz(0)).toBe(0);
  });
});

```

- to link to the `.js` file

```js
//to make the first test pass first
module.exports.fizzBuzz = () => {
    return 0;
};
```

----------------

#### Red, Green, Refactor

- ##### When is a good time to commit code?

  - red => failing
  - green => shitty code that make it pass
  - commit your code
  - refactoring, make code readable and maintainable
  - make sure test is still passing
  - commit code, say what you refactor



#### Testing pyramid

<img src="https://cdn2.hubspot.net/hubfs/208250/Blog_Images/uiauto1.png" alt="img" style="zoom:65%;" />



- Unit test = testing business sense functionality, rather than the internal implementation

```js
//this function is known as internal implementation (helper methods) = usually not tested on 
checkLength(string, length){
    return string.length >= length
}

//this function is more for business sense functionality, thus is usually tested
PasswordValid(pw){
    if (passwordLengthGt8 = checkLength(pw,8)){
        return true
        }
    return false
}
```



- Integration test = typically for UI work = contained within application 
- E2E (End to end) = testing with the 3rd party libraries i.e other APIs



- ##### Difference between TDD and Unit Testing 

| Test Driven Development                                      | Unit Test                                                    |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1. Write a test & make it fail for the right reason<br />2. Write just enough code to make the test pass<br />3. Relook at the code and improve the structure without touching the test | Testing functionality for a smallest meaningful chunk of code, |

