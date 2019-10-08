20 sept 2019

## React Router

- single post application
- able to change the page without re-rendering the entire page 

https://reacttraining.com/react-router/web/guides/quick-start

##### installation

```bash
npm install react-router-dom
```



```react
//things to import
import{
    BrowserRouter as Router,
    Route,
    Link, 
    Switch, 
    Redirect,
} from "react-router-dom"
```



```react
<header>
    <Link to={"/"}>Home</Link>
    <Link to={"/Apple"}>Apple</Link>
</header>

//element that will be replaced
<switch>
    <Route path="/" component{()=> <div>Hello World</div>}/>
    <Route exact path={"/apple"} component{()=> <Apple/>}/>
    <Redirect to="/">
</switch>
        
//possible to use this.        
<Route path={"/"} component={()=><div><h1>404 Page Not Found</h1></div>} ></Route>
```



