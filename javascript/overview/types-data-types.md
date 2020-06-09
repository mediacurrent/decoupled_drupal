# Types / Data Types

Types group together similar values that can have common operations performed on them. For example, you can multiply values: `0, 1, 1, 2, 3, 5, 8, 13`,  however you could not multiply: `horse, andrew garfield, onions`. 

Conversely you could merge `horse, andrew jackson, onions` but not the number sequence. These are examples of the types `number` and `string`and how they support different operations.

The type of a value determines the operations and methods that are allowed to be called on it. These are the types in JavaScript**:**

### Data Types

#### number

The number type represents integers and floating point numbers \(floats\), so 42 or 41.95.

There are also special numeric values that are part of the number type: Infinity and NaN.  NaN is the result of computational error usually when an operation is incorrectly applied.  For example, if you tried to divide a string with a number 

```javascript
console.log (“horse” / 42); //result: nan
```

#### **string**

A string is surrounded by quotes. There are two types of quotes, simple and extended functionality. Simple quotes are either single or double quotes. There is no functional difference.  

`"item", 'item'`

Extended functionality quotes are ```backticks``` that allow us to embed variables into to strings.

```javascript
let animal = ‘horse’; 
console.log(`animal type is ${animal}`) // animal type is horse.
```

In this case animal variables become part of the string.

#### **bigInt**

This type allows us to represent whole numbers larger than 253 - 1, which is the largest number that Javascript can reliably represent.

A BigInt is created by adding n to the end of an integer or by calling the function BigInt\(\).

_Currently BigInt is not supported in Safari and IE._

####  **boolean**

The boolean type has two reserved words: `true` and `false`. Booleans are used for their comparison operations == \(is equal to\), &gt; \(greater than\), &lt; \(less than\) etc. 

Booleans also accept **truthy** and **falsy** values which evaluate to either true or false.

Falsy values:

* False
* -0
* 0
* ‘’ or “” an empty string
* null
* undefined 
* NaN

Any other value can be considered truthy, including:

* ‘0’ a string of a single zero.
* ‘false’ a string that contains the text false.
* \[\] and empty array
* {} and empty object

#### undefined

Undefined indicates that the value is not assigned. Example:

```javascript
let  animal;
alert(animal); // undefined
```

#### **Symbol**

Symbols are completely unique identifiers. They can be used to prevent name clashing in object keys. It can also used to prevent object properties to be enumerable.

### Types

#### null

Null indicates the absence of a value.

#### Function

Functions are programs that perform a particular task, they are executed when called. They can be passed values to be used within the function. Functions also return a value. We go deeper into functions later. As a type, functions are objects.

#### Object

Objects are different from other types, which can be considered ‘primitives’ \(string, number, boolean, symbol, null and undefined\)  as they contain only one thing. Objects can contain collections of data.

```javascript
var horse = {
  name: "Trigger",
  legs: 4,
  color: "black"
};
```





