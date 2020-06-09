# Classes

### Review Prototypes/Inheritance

In the [prototype / inheritance](../overview/prototypes-inheritance.md) section we talked setting up and adding to prototypes.

```javascript
// Contruct the prototype. 
function PrototypicalGreeting(greeting = "Hello", name = "World") {
  this.greeting = greeting
  this.name = name
}

// Add the return to the prototype.
PrototypicalGreeting.prototype.greet = function() {
  return `${this.greeting}, ${this.name}!`
}

const greetProto = new PrototypicalGreeting("Hey", "folks")
console.log(greetProto.greet()) // Hey Folks

```

The most important difference between classes and prototype-based inheritance is that a class defines a _type_ which can be **instantiated at runtime**, whereas a prototype is itself an object instance.

A child of an ES6 class is another _type_ definition which extends the parent with new properties and methods, which in turn can be **instantiated at runtime**. A child of a prototype is another object _instance_ which delegates to the parent any properties that aren’t implemented on the child.

Let's look at classes vs constructor functions.

```javascript
// Initializing a constructor function
function HorseRider(name, bibColor) {
    this.name = name;
    this.bibColor = bibColor;
}

// How this looks as a class.
class HorseRider {
    constructor(name, bibColor) {
        this.name = name;
        this.bibColor = bibColor;
    }
}
```

When we worked on constructor functions we added methods to the prototype. With classes you can added them directly to the class.

```javascript
// Initializing a constructor function
function HorseRider(name, bibColor) {
    this.name = name;
    this.bibColor = bibColor;
}

// Add a method to the constructor function.
HorseRider.prototype.summary = function() {
 return `${this.name} wears a ${this.bibColor} bib`;
}

// How this looks as a class.
class HorseRider {
    constructor(name, bibColor) {
        this.name = name;
        this.bibColor = bibColor;
    }
    
    // Add a method to the class.
    summary() {
        return `${this.name} wears a ${this.bibColor} bib`;
    }
}
```

Using our class:

```javascript
class HorseRider {
    constructor(name, bibColor) {
        this.name = name;
        this.bibColor = bibColor;
    }
    
    // Add a method to the class.
    summary() {
        return `${this.name} wears a ${this.bibColor} bib`;
    }
}

const newRider = new HorseRider('Andrew', 'red');
// Will return Andrew wears a red bib
// This has this as it's prototype: 
// __proto__:
//  constructor: class HorseRider
//  summary: ƒ summary()
```

The above shows that the functions were applied to the prototype, which is a little less syntax than the constructor function approach.

In our prototype inheritance section, we created a child  based on a parent:

```javascript
function jockeyInRace(name, racesEntered, racesWon, bibColor, homeTown) {
  horseInRace.call(this, name, racesEntered, racesWon);
  this.bibColor = bibColor;
  this.homeTown = homeTown;
}
```

Here you can see the .call\(\) function is using the properties for the parent in the child, and adding its variances. With classes, we can achieve the same thing like this:

```javascript
// Creating a new class from the parent
class HorseRidden extends HorseRider  {
    constructor(name, bibColor, color) {
        // Chain constructor with super
        super(name, bibColor);

        // Add a new property
        this.color = color;
    }
}

const newHorse = new HorseRidden('Last Man Standing', 'orange', 'gray');
```

The `extends` keyword is used to create a new class, that is a child of another class. So here, **HorseRidden** is a child of **HorseRider**.  They keyword `super` is used to access the functions of the parent, so here name and bibColor. 

Classes are a little less syntax to define, and have the advantage or being used at runtime.

{% hint style="info" %}
[https://www.toptal.com/javascript/es6-class-chaos-keeps-js-developer-up](https://www.toptal.com/javascript/es6-class-chaos-keeps-js-developer-up)
{% endhint %}



