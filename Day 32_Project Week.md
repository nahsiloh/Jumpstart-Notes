15th Oct 2019

## Project Week

##### Architecture

1. Define what routes your frontend needs
2. Design your routes based on those requirements
3. Define your resources
4. Model your resources
5. Defining the protected routes 



##### Previous codes

```js
// in add_location_for_each_day.js
addOneLocation = () => {
    this.setState({
      listOfLocationsPerDay: [
        ...this.state.listOfLocationsPerDay,
        { id: uuidv1(), destination: "", program: "", cost: "" }
      ]
    });
  };

updateLocation = (
    travelDetail,
    inputDestination,
    inputProgram,
    inputCost
) => {
    travelDetail.destination = inputDestination;
    travelDetail.program = inputProgram;
    travelDetail.cost = inputCost;
    this.setState({
        listOfLocationsPerDay: [...this.state.listOfLocationsPerDay]
    });
};

deleteLocation = travelDetail => {
    this.setState({
        listOfLocationsPerDay: [
            ...this.state.listOfLocationsPerDay.filter(
                item => item !== travelDetail
            )
        ]
    });
};
```



### Lessons and challenges

1. **Deciding on the backend data structure**
   - Option A
     - storing individual input box to the server
     - no loss of data as every item will be saved once confirmed
   - Option B
     - storing the entire trip at once
     - Trip with a subdocument Itinerary
     - may have loss in data if user clicks refresh/ close the page

2. **Formatting the frontend data to match the backend data to display and save**
   - require a thorough understanding of the structure of the states and the backend schema
3. **Passing of states in child components to parent to save in the server**
4. **Using of browser local storage to save the changes**
   - data is persisted on the browser
   - ideal for a travel app as sometimes there might not be wifi signal. App can function in offline mode.
5. **Benefits of Testing**
   - as the app grows bigger, it is difficult to keep track of the bugs and issues, as changing one thing might affect another







