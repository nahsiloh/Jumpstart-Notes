7th Oct 2019

## Backend

- Datastore

  - Types of data stores
  - Modeling your data
  - Mongo DB
  - Mongoose - layer over the database
    - separate API that JS talks to the database e.g the model
    - converts JS to SQL so that we can speak to the data base 

- Authentication 

  - - required because HTTP is stateless thus require other forms of authentication to verify the client

  - Storing passwords 
    - password encryptions
  - Json web tokens

- Deploy to production 

  - Heroku - `npm run start`
    - will provide a port number
  - Port number, Environment variables  
    - automate process that changes the port automatically depending on whether we are in development, test or production environments (min. 3 environments)
    - development - my own computer (local) 
    - test - environment to reliably create test 
    - production - actual code that the customer will use 
  - CORS

-----------------

#### Types of Data Stores

1. **flat files** = CSV

   | ID   | Title       | Author | Publisher |
   | ---- | ----------- | ------ | --------- |
   | 1    | My 1st Book | Bob    | Penguin   |
   | 2    | My 2nd Book | Bob    | Penguin   |

   

2. **Relational (SQL)**

   - preferred for structured data
   - relational style requires multi-tables
   - faster in the long run, after all the data is structured

   - when there is a relationship between one table to another 

   ##### Book 

   | ID (primary id) | Title       | Author Id (foreign id) |
   | --------------- | ----------- | ---------------------- |
   | 1               | My 1st Book | 1                      |
   | 2               | My 2nd Book | 1                      |

   ##### Author 

   | Author Id (foreign id) | Name | Tel          |
   | ---------------------- | ---- | ------------ |
   | 1                      | Bob  | +18009999999 |
   | 2                      | John | +18009887777 |

   - SQL = language query tables
   - ORM = a wrapper that translates code to SQL, which the database can read

   

   - Normalization of the data
   - ERM - entity relational diagrams
     - one- to-one
     - one-to-many
     - many-to-many

   

3. **Non-relational (NoSQL)**

   https://aws.amazon.com/nosql/

   - eg. mongodb - Document 

   - in data that is changing, fluid, do not know what information is going to be inside (unstructured)

   - many different forms of non-relational databases 

     

###### Comparison between relational and one type of non-relational

| Relational                                                   | Non-Relational <br />(Document )                             |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Tables/ Entitites                                            | Collections                                                  |
| Row/entries                                                  | Documents                                                    |
| *Author title*<br />ID      Name<br />1        Bob<br />2        John | *Author collection*<br />{ID: 1                              {Apple:5<br />  Name: Bob                    Banana:[ ]<br />}                                       } |



##### Mongoose 

- schema
- ODM



##### Mongo db and Mongoose

- mongoose creates a structure(schema) for mongo db

```
Author
{
Id: 1(Obj)
Name: Bob(str)(1)(R)
}
```



##### ORM vs ODM

- **ORM** is used to translate between your objects in code and the **relational representation** of the data

- **ODM** is used to to translate between your objects in code and the **document** representation of the data, where the **document is an object or JSON-like document**

- used to translate to any language that the database speaks. Depending on the ORM, may support multiple database languages, thus will be able to translate/ switch databases from eg. MySQL to PostGres

  

  ###### ![1570438436951](C:\Users\lisha\AppData\Roaming\Typora\typora-user-images\1570438436951.png)

