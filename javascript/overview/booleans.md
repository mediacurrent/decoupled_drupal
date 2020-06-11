# Booleans

We discussed booleans earlier as part of [types](types-data-types.md#boolean). Booleans evaluate as either `true` or `false`, but in javascript there are things that can be considered true or false outside of the keywords `true` and `false`. These values are called **truthy** and **falsy**.

These values are always falsy: 

```javascript
horse = 0; // This is false
horse = false; // This is false
horse = ''; // This is false
horse = null: // This is false
horse = undefined; // This is false
horse =  NaN; // This is false

if (horse === true) {
  console.log('This is true');
}

else {
  console.log('This is false');
}
```

So when checking if the value is true, as above we are saying :

```javascript
if (horse) {
  console.log('This is true');
  // horse could be '0' 'false' (both strings, not an integer or keyword), [], {} etc.
}

else {
  console.log('This is false');
  //horse could be any of the values including false, 0, '', null, NaN, undefined. 
}
```

#### Equality Comparisons

Comparisons will always return a boolean value but as you can see, testing if something is true or not is nuanced. When writing evaluations we need to make sure that we are taking the necessary steps to ensure we are getting the correct value. 

Non strict equality checks can have issues with evaluation.

```javascript
console.log( 5 == 5 ); // true
console.log( '5' == 5); // true
```

Above we see that it will evaluate a string with a number, which are different types. We should want to make sure that we are comparing types, which is where **Strict Equality**, or `===` is used.

```javascript
console.log( 5 === 5 ); // true
console.log( '5' === 5); // false
```

Strict equality will not return true for different types. This is also true of non equality checkers.

```javascript
// != and !== are asking if the first value is not equal to the second.
console.log( '5' != 5 ); // false
console.log( '5' !== 5); // true
```



