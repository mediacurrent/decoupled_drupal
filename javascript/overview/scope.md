# Scope

Scope in javascript is the accessibility of functions, objects and variables to parts of your code at runtime.

The next chapter [**Variables**](variables.md#variable-scope) has examples of scoping and how variable declarations impact the scope.

Here is an illustration of scope as it appears in code:

```javascript
// global scope

var horse = 'gerald';

function numberOfHorses() {

    // function / local scope
    console.log( horse ); // gerald.

    horse = 'reggie';
    console.log( horse ); // reggie

    function numberOfGrayHorses() {

        // function / local scope 2
    }
}

// global scope
console.log( horse ); // gerald.

if (horse) {
    var weHaveHorse = true;
}

console.log(weHaveHorse); // true
numberOfHorses();
```

#### Global scope 

This is the scope when you are not inside a function. Defining a variable here means that it is available out side of any functions.

#### Local scope

Locally scoped variables defined inside a function get a different scope each time the function is called. In our example above, we can see that defining horse inside this function only retains the new value within that function.

#### Block Statements

In our above example, the block statement `if` doesn't create a new scope. So the variable defined here will remain in the current scope, which in our example is global. Other block statements include `for`, `while` and `switch`.



