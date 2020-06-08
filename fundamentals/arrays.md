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
let horses = ['tony', 'lenny', 'henry', 'jessica', 'sharon', 'pete davidson']

// First item:
horses[0]; // tony
//Last item:
horses[horses.length -1]; // pete davidson
//Note that is is a syntax error:
horses.0;
```

