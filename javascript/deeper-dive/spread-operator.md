# Spread Operator

We can use something called the spread operator to make some of coding tasks easier. For example, if we want to pass in a set of parameters, rather than redefine them in the function call we can do this:

```javascript
function jockeyFacts (name, currentHorse, favFood) {
  console.log(name);// Humberto Milan
  console.log(currentHorse); // Fast Freddie
  console.log(favFood) // Cakes
}

let jockey1 = ['Humberto Milan', 'Fast Freddie', 'Cakes']

jockeyFacts(...jockey1);
```

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

