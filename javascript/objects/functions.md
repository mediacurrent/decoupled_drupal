# Functions

There are a few ways to define functions. 

#### **Function Declaration** 

This defines a named function. 

```javascript
function nameOfFunction(parameters){
  /* do this /*
}
```

This method 'hoists' the function, allowing it to be called before it is defined.  As with variables, the function defined this way, is moved silently by javascript to the top of its scope.

```javascript
nameOfHorse('Stephen');

function nameOfHorse(name) {
  console.log(name) //logs Stephen
}
```

#### **Function Expression** 

Defines either a named or anonymous function. Above we defined a named function `nameOfHorse`. An anonymous function is a function that has no name. Function expressions are not hoisted and can not be called before they are defined. 

```javascript
let nameOfJockey = function(name) {
  console.log(name)
} //anonymous function

let nameOfJockey = function jockeyName(name) {
  console.log(name)
} //named function
```

#### Arrow Function Expression

Arrow functions are a short syntax for anonymous functions. Arrow functions retain the scope of the caller, so do not create their own `this`

```javascript
let raceTrackName = (name) => {
  console.log(name);
}
```

#### Calling \(invoking\) Functions

Functions are executed when called, also know as invoking. You can execute a function by referencing the name of the function followed by parenthesis. From our example above:

```javascript
nameOfHorse('Stephen');
```

If the function has no parameters, you can invoke it with empty parenthesis.

```javascript
function racesWon() {
  console.log("this horse has won no races");
}

racesWon();// this horse has won no races
```

#### Functions and Return

The return will end the function execution and specify the value to be returned. 

Functions with that don't declare their return will return `'undefined'` . 

```javascript
function noReturns(){}; // no defined return 

noReturns(); //undefined
```

If we want to return a value, we would declare it like this:  


```javascript
function withReturns(){ 
  return true;
}; // return defined as 'true' 

withReturns(); // true
```

The return value is used by the initiator, the most common example of this in action is

```javascript
let nPlus1 = function(n) {
  return n + 1;
};

let current = nPlus1(1);

console.log(current); // 2
```

Here we have returned a value from our function and assigned it to our variable `'current`'. A return statement will immediately stop the invocation of the function, so if our above function structured like this:

```javascript
let nPlus1 = function(n) {
  return n + 1;
  return n * 4;
};

let current = nPlus(1);
```

The value of current would still be 2 because the first return ends the function before the second line is reached.

