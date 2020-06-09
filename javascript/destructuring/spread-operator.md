# Spread Operator

### =

Arrays and objects can be combined using the spread operator.

```javascript
let winnersRace1 = ['Jerry', 'Paul III', 'Harry']

let winnersRace2 = [ 'Terry', 'Francis', 'Jessica']

let winnersThisSeason = [ ...winnersRace1, ...winnersRace2 ];

console.log(winnersThisSeason); // ["Jerry", "Paul III", "Harry", "Terry", "Francis", "Jessica"]
```

```javascript
let winnersRace1 = {
  1: 'Jerry', 
  2: 'Paul III',
  3: 'Harry'
}

let winnersRace2 = {
  4: 'Terry',
  5: 'Francis', 
  6: 'Jessica'
};

let winnersThisSeason = { ...winnersRace1, ...winnersRace2 };

console.log(winnersThisSeason); // Object { 1: "Jerry", 2: "Paul III", 3: "Harry", 4: "Terry", 5: "Francis", 6: "Jessica" }
```

Arrays ands objects can be cloned with the spread operator.

```javascript
let winnersRace1 = {
  1: 'Jerry', 
  2: 'Paul III',
  3: 'Harry'
}

let winnersRace2 = {
  ...winnersRace1
};

console.log( winnersRace2 ); // Object { 1: "Jerry", 2: "Paul III", 3: "Harry" }
```

```javascript
let winnersRace1 = [ 'Jerry', 'Paul III', 'Harry' ];

let winnersRace2 = [
  ...winnersRace1
 ];

console.log( winnersRace2 ); // ["Jerry", "Paul III", "Harry"]
```

