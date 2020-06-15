# Variables

A variable is a named container for reusable data. Before es6 we would declare a variable by use the keyword `var`. With es6 we also have two new keywords: `let` and `const`. 

```javascript
var horseName = 'Little Sebastian';
let horseColor = 'dappled';
let horseType; 
const horseAge; 
```

These are examples or variable declarations, you can choose not to assign values to variables if you are not ready for them to contain data. Variables are initialized when they are declared, allocating memory to the engine. Variables are assigned when they have an assignment operator `=` . By doing this we are giving the variable a data [type](types-data-types.md), in the above example they are both `string` .

### Naming Variables

Variable names should use [lowerCamelCase](https://eslint.org/docs/rules/camelcase) and should not contain symbols or begin with numbers.

### Variable scope

Scope defines where the variables are accessible within the script. Variables are either globally scoped or scoped to the function it was created in. 

```javascript
function planRace () { 
  // local / function scope
  var eventLocation = 'My Race Track';
  return eventLocation;
}

// back to global scope

console.log(eventLocation) //  Reference Error 
```

Accessing the `eventLocation` variable outside of the `planRace` function returns a reference error because it is only scoped to the function.

If we were to extend that function, we can see how block scoping, works with in functions.

```javascript
function planRace (locations) { 
  var eventLocation = [];
  // local / function scope
  console.log(newLocation); // undefined

  for(var i = 0; i < locations.length; i ++) {
  // new locations is in a block, so is know to the function scope, but
  // is undefined until here.
   var newLocation = locations[i];
   eventLocation.push(newLocation);  
  }
  
  // Still part of the local / function scope
  console.log(i); // 2
  console.log(newLocation); // Kentucky
  return eventLocation;
}

planRace(['My house', 'Kentucky']);
```

Here you can see that with in the function , newLocation is undefined and not a reference error because of how vars are treated by the function scoping \(this is called **hoisting**\). Within the function block the newLocation and i variables are accessible when defined with the `var` keyword.

When we use the word '**hoisting**' we mean that javascript has moved the variable declaration to the top of the scope silently, or '**hoisted**' it. The above to javascript looks like: 

```javascript
function planRace (locations) { 
  var eventLocation = [];
  var newLocation;
  var i;
  ...
```

If we are using strict mode, hoisting will not work, so variables called before they are defined will return a reference error vs. undefined. We will also see how functions are affected by hoisting in the [functions](../objects/functions.md) section.

### Let

One of the key differences between the `var` keyword and the `let` keyword is that variables created with `let` are available within in the block and are not scoped to the function. So if we update our function: 

```javascript
function planRace (locations) { 
  // local / function scope
  let eventLocation = [];
  
  console.log(newLocation); // Reference Error: newLocation is not defined

  for(let i =0; i < locations.length; i ++) {
  // blocks scope
   let newLocation = locations[i];
   eventLocation.push(newLocation);  
  }
  
  console.log(i); // Reference Error: i is not defined
  console.log(newLocation); 
  return eventLocation;
}

planRace(['My house', 'Kentucky']);
```

Now we are unable to access i outside of the block it is declared in, because `let` has different scoping properties to `var`. 

### Const

Const and let share the same block scoping behavior. The difference between that you can't reassign its value once it is set.

```javascript
let horseName = 'andrew';
horseName = 'stuart'; 
console.log(horseName); // stuart

const horseName = 'chucky';
horseName = 'cedric'; //Uncaught SyntaxError: Identifier 'horseName' has already been declared 
```

Sometimes you will see that `const` is referred to as immutable which isn't always the case. When an object is defined with const, its properties can be updated or mutated, which is an important distinction.

```javascript
const horseStats = {
 height: "13 hands",
 speed: "very very fast",
 color: "a deep ochre"
};

console.log(horseStats.color); // a deep ochre

horseStats.color = 'black';


console.log(horseStats.color); // black
```



### When to use Let Const or Var

You shouldn't need to use `var` now that we have `let` and `const`. 

Whether you default to always const or always let until the other is necessary is an ongoing debate. We tend to default to const unless using something like a for loop. You can read both sides of the argument [here](https://css-tricks.com/let-vs-const/). The important thing is to consider the use case as you develop.

