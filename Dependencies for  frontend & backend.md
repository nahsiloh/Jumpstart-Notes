## Starting backend

1. `npm init -y`

2. `npm install express mongoose cors dotenv`

3. Developer dependencies

   `npm install --save-dev nodemon eslint eslint-plugin-jest cross-env`

4. if there is user login page that requires authentication

   `npm install jsonwebtoken bcryptjs cookie-parser` 

5. For testing

   `npm install --save-dev jest supertest mongodb-memory-server`

   

## Starting frontend

1. `npx create-react-app <app name>`

2. `npm install axios react-router-dom`

   

## Axios

`npm install axios`

Connecting the frontend to the backend

```js
//in the front end
import axios from "axios"

// sending information to the backend
axios.post("http://localhost:5000/users/add", user)
	.then(res => console.log(res.data))


//getting information from the backend to create a drop down menu to get all the users
componentDidMount(){
    axios.get("http://localhost:5000/users")
    	.then(res=>{
        if (response.data.length >0){
            this.setState({
                users: response.data.map(user=> user.username)
                username: response.data[0].username
            })
        }
    })
}

//deleting item and returning the remaining as a filtererd array
deleteExercise(id){
    axios.delete("http://localhost:5000/exercises/" + id)
    	.then(res=>console.log(res.data))
    
    this.setState({
        exercises: this.state.exercises.filter(el=>el._id !== id)
    })
}
```

