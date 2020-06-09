# Spread Operator

### =

### Object/Array Combining

Array ands objects can be cloned with the spread operator.

```javascript
let winnersRace1 = [ 'Jerry', 'Paul III', 'Harry' ];

let winnersRace2 = [
  ...winnersRace1
 ];

console.log( winnersRace2 ); // ["Jerry", "Paul III", "Harry"]
```

