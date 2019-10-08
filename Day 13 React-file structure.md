18 sept 2019

## Structuring React

- in src = Assets, Common & Components folder
- Assets = place Javascript data 
- Common = where it is reusable items, example headers
- Components = specific related functions



#### Lifecycle Methods

![1568793747327](C:\Users\lisha\AppData\Roaming\Typora\typora-user-images\1568793747327.png)



- changing of this.state triggers a re-render

```react
//onClick is a JSX function
onClick = {() =>{
    this.setState((states => {
        return {counter:states.counter +1}
    })
}}
```



- call back in setState

```react
next=()=>{

}
```

