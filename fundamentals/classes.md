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

Let's look at classes.

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

{% hint style="info" %}
[https://www.toptal.com/javascript/es6-class-chaos-keeps-js-developer-up](https://www.toptal.com/javascript/es6-class-chaos-keeps-js-developer-up)
{% endhint %}

### super

### constructor

### extends

