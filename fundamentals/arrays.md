# Arrays

Arrays are objects whose prototypes have methods to perform array relevant operations. The length of an array can change at any time. Arrays can not use strings as indexes, as seen in our [objects](untitled.md) section, but must use integers :

```javascript
let horse = [
  'string identifier': 'nope',
  1 : 'yes'
]  
```

### Operator examples:

```javascript
let raceTypes = [ 'flat', 'jump', 'harness', 'saddle trot', 'endurance' ];

// Get length
console.log(raceTypes.length); // 5;

// Get last item.
let lastType = raceTypes[raceTypes.length -1]

console.log(lastType); //endurance

// Add to end of array
raceTypes.push('street rules');

console.log(raceTypes); // 'flat', 'jump', 'harness', 'saddle trot', 'endurance', 'street rules'

// Remove from the end of an array ( removing the previously added 'street rules')
raceTypes.pop();
console.log(raceTypes); // 'flat', 'jump', 'harness', 'saddle trot', 'endurance'

// Add to the begining of an array
raceTypes.unshift('sack');
console.log(raceTypes); // 'sack', 'flat', 'jump', 'harness', 'saddle trot', 'endurance'

// remove from the beginning of an array.
raceTypes.shift();
console.log(raceTypes); // 'flat', 'jump', 'harness', 'saddle trot', 'endurance'

//Find an index of an item.
raceTypes.indexOf('jump'); // 1

//Remove a specific index.
raceType.splice( pos, 1); // 'flat', 'harness', 'saddle trot', 'endurance'

//copy an array
let newRaceTypes = raceTypes.slice();
```

### Accessing Arrays

Arrays are zero indexed. This means that the first item in the array has an index of 0.

```javascript
let horses = ['tony', 'lenny', 'henry', 'jessica', 'sharon', 'pete davidson'];

// First item:
horses[0]; // tony
//Last item:
horses[horses.length -1]; // pete davidson
//Note that is is a syntax error as dot notation cannot be used:
horses.0;
```

### Map

Map is a way to iterate over an array. Map creates a new array that avoids mutation. In the below example you can see how we take an array of winnings represented as integers and pass them through a function, and then map the results to a new array. We have also preserved the original array.

```javascript
let tonyTheHorseWinnings = [100, 1000, 200, 5, 4000];

let convertToCanadianDollars = item => item*2;

let tonyTheHorseWinningsCanadian = tonyTheHorseWinnings.map(convertToCanadianDollars);
 //[200, 2000, 400, 10, 8000]
```

Map is popular in React for rendering lists.

```javascript

const horses = ['tony', 'lenny', 'henry', 'jessica', 'sharon', 'pete davidson'];

const horseList = () => (
  <div>
    <ul>{horses.map(horse => <li key={horse}> {horse} </li>)}</ul>
  </div>
);

```

This works if we want to render the entire array, but sometimes we only need a part of it. This is where filter comes in.

### Filter

If we have an array of race winners, and the amount of wins they have, we can filter that data to get different subsets. So if we want to only know about winners who have won more than 10 races we might do this:

```javascript
const winners = [
  {
    name: "lloyd",
    wins: 9
  },
  {
    name: "andrew",
    wins: 12
  },
  {
    name: "susan",
    wins: 16
  },
];

const overTen = winners.filter( champs => champs.wins > 9 );
//{ name: "andrew", wins: 12 }, { name: "susan", wins: 16 }
```



