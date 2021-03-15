## JS this in constructors
In JavaScript, a function call with a new operator in front of it turns it into a constructor call. When a function is invoked as a constructor, a brand-new object is created for us automatically, and that new object is then used as the ‘this’ binding for the function call.

In our example, we are initializing the new object by setting the two properties firstName and lastName. If I put in a couple of log statements, we can trace how the person object is put together step by step.

```JS
function Person(firstName, lastName) {
    console.log(this);
    this.firstName = firstName;
    console.log(this);
    this.lastName = lastName;
    console.log(this);
}
```

const person = new Person("Jane", "Doe");
We also see the name of the constructor function in the console output.

### Console output


This shows us that our new object has been linked to the Person function's prototype. Notice that our Person function doesn't contain a return statement. In that case, the brand-new object that was constructed for us is returned automatically.


### invisible return


You can imagine an invisible return this; statement at the end of the function. We can also return an entirely different object from the constructor function.

```JS
function Person(firstName, lastName) {
    this.firstName = firstName;
    console.log(this);


    return {
        firstName: "John",
        lastName: "Roe"
    };
}
```

const person = new Person("Jane", "Doe");
console.log(person);
After we return from the function, the newly-created object that we previously initialized is lost because it's out of scope and nobody has a reference to it anymore.

### foo
