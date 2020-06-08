# Classes

### Review Prototypes/Inheritance

```javascript
function PrototypicalGreeting(greeting = "Hello", name = "World") {
  this.greeting = greeting
  this.name = name
}

PrototypicalGreeting.prototype.greet = function() {
  return `${this.greeting}, ${this.name}!`
}

const greetProto = new PrototypicalGreeting("Hey", "folks")
console.log(greetProto.greet())

class ClassicalGreeting {
  constructor(greeting = "Hello", name = "World") {
    this.greeting = greeting
    this.name = name
  }

  greet() {
    return `${this.greeting}, ${this.name}!`
  }
}

const classyGreeting = new ClassicalGreeting("Hey", "folks")

console.log(classyGreeting.greet())
```

{% hint style="info" %}
[https://www.toptal.com/javascript/es6-class-chaos-keeps-js-developer-up](https://www.toptal.com/javascript/es6-class-chaos-keeps-js-developer-up)
{% endhint %}

### super

### constructor

### extends

