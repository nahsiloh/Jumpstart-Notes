18 nov 2019

## OOP

For coding interviews:

- `npm install --save-dev jest eslint`
- change scripts for test and `"test:watch": test --watch` 



#### Code Completion

- [x] solving the problem
- [ ] no logs
- [x] refactoring - readability, variable names, separate functions, no magic numbers
- [x] test
- [ ] linting 
- [ ] edge cases
- [ ] negative scenarios



#### Design and Object-oriented programming

- Turing
- Assembly language
- Dijkstra (structured programming) - if, else, while
- procedural programming - separating into components/ functions - only run codes through a function
- functional programming - not using variables, Event sourcing



##### 4 pillars of OOP

1. **Encapsulation** - hiding the data from the person who calls the function

2. **Abstraction** - exposing what needs to be exposed (methods that can be called)

   

   **Law of Demeter** - do not show the exact steps to execute a call. Instead, create a new function to handle that. 

   eg. paying the cashier. Instead of shopper.getWallet().deduct(2), shopper.payAmount(2)

   ```js
   class Wallet {
     constructor(value) {
       this.moneyInWallet = value;
     }
   
     takeOutMoney(value) {
       this.moneyInWallet -= value;
     }
   }
   
   class Shopper {
     constructor() {
       this.wallet = new Wallet(5);
     }
   
     getWallet() {
       return this.wallet;
     }
   
     payAmount(value) {
       this.wallet.takeOutMoney(value);
     }
   }
   
   const shopper = new Shopper();
   shopper.payAmount(2);
   ```

   

3. **Inheritance** - D.R.Y - don't repeat yourself

   - **Favour composition over inheritance** - eg. shopper containing wallet (composition) rather than extending from wallet (inheritance)

   - use inheritance when there is a strong relationship

     

4. **Polymorphism** - method can take many different forms based on an object

   - from example below, the calculateSurface() function is overwritten. Thus showing that the function allows for polymorphism

   ```js
   class Figure{
       calculateSurface(){
           throw new Error
       }
   }
   
   class Triangle extends figure{
       constructor(){
           super()
           this.base = base
           this.height = height
       }
       calculateSurface(){
           area = 0.5*base*height
       }
   }
   
   const triangle = new Triangle(5,10)
   triangle.calculateSurface()
   ```

   

   ### SOLID principles

   https://www.youtube.com/watch?v=XzdhzyAukMM
   
   - **S** - **SRP** - single responsibility principle
     - a class should have only one reason to change, meaning that a class should have only one job
     - often break the D.R.Y principle
     
   - **O** - **OCP** - open/closed principle
     
     - when extensions are added and the code breaks 
     
     - objects or entities should be open for extension and closed for modification
     
  - ```js
       // BAD
       //there is no way to change the iceCreamFlavors without modifying the existing array of iceCreamFlavor
       var iceCreamFlavors=["chocolate","vanilla"];
       var iceCreamMaker={
        makeIceCream (flavor) {
         if(iceCreamFlavors.indexOf(flavor)>-1){
          console.log("Great success. You now have ice cream.")
         }else{
       console.log("Epic fail. No ice cream for you.")
         }
     }
       }
    export default iceCreamMaker;
       
       // GOOD
       //a function addFlavor allows one to add flavors by calling the function without changing the base file
       var iceCreamFlavors=["chocolate","vanilla"];
       var iceCreamMaker={
        makeIceCream (flavor) {
         if(iceCreamFlavors.indexOf(flavor)>-1){
          console.log("Great success. You now have ice cream.")
         }else{
          console.log("Epic fail. No ice cream for you.")
         }
        }
        addFlavor(flavor){
         iceCreamFlavors.push(flavor);
        }
       }
       export default iceCreamMaker;
       ```
     
       
     
   - **L** - **LSP** - Liskov substitution principle
     - when an object is extended, should be able to substitute parent class without breaking any code functionality
     - meaning the extended child class shares the same properties/ similar behaviors as the parent. eg. a bicycle should not be classified under a vehicle which uses petrol
     - if the child can fly but the parent cannot fly, but both the child and parent can walk, this still maintains LSP
     - i.e child should be able to perform all parent functionalities, but child can do more
     - child cannot be stricter than the parent
   
   - **I** - **ISP** - interface segregation principle
     - when creating and implementing the interface, require to implement everything within the interface
     - interface is a set of implementation "rules" for an object
     - eg. an electric car will break the ISP if it extends car as electric car uses battery instead of fuel. Thus cannot top-up fuel = i.e should split the interface
     
   - **D** - **DIP** - dependency inversion principle
     
     - eg. bluetooth, where the connection can be created when required
     - when things are not connected to a solid object, but by an abstraction
     - its alright to be broken if the connection is highly unlikely to change
   
   
   
   
   
   