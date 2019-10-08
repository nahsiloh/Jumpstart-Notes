4th Oct 2019

## Express

##### Guard clauses

```js
//inside test file
describe("parseQueryToString",()=>{
    it("should returns ? when an empty query object is passed",()=>{
        expect(parseQueryToString()).toBe("?")       
    })
})
```



```js
//in the function to get the 1st test to pass
if (!query) {
    throw new Error("Please include a query, dammit!");
}

if (Object.entries(query).length === 0) {
    return "?";
}
```



##### Error Handling

https://expressjs.com/en/guide/error-handling.html



##### mockReturnValueOnce vs mockImplementationOnce

