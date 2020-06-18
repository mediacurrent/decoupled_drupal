---
description: >-
  Deconstructing lets us break down complex structures into more easier to
  manage parts.
---

# Destructuring

## Arrays

We can destructure an array into variables like so:

```javascript
// Our array will remain unmodified
let raceFinishers = ['Gary', 'Lenny', 'Karl', 'Hans', 'John']

// Assign our results
let [firstPlace, secondPlace, thirdPlace, fourthPlace, fifthPlace] = raceFinishers;

// Who was third?
console.log(thirdPlace); //Karl

// We can also deconstruct this string
let raceWinners = 'Gary ridden-by Harmless Harry';

// Get the separated results
let [horseWinner, riderWinner] = raceWinners.split('ridden-by');

console.log(horseWinner); // Gary 
console.log(riderWinner); // Harmless Harry
```

As demonstrated above we can also use methods that return arrays such as split. It is important to note that the original array is not modified.

We can also act on parts of the data:

```javascript
// Our array will remain unmodified
let raceFinishers = ['Gary', 'Lenny', 'Karl', 'Hans', 'John']

// We can skip entries like so:
let [firstPlace, ,thirdPlace] = raceFinishers;

console.log(firstPlace, thirdPlace); //"Gary" "Karl"

// Using the rest operator, we can add all results that are not 1, 2, 3 to a new 
// array.
let [tenPoints, eightPoints, sixPoints, ...didNotGetPoints] = raceFinishers;

console.log(didNotGetPoints); //["Hans", "John"]
```



## Objects

We can also destructure objects:

```javascript
let gerryStats = {
  name: 'Fast Gerry',
  height: '16 hands',
  color: 'Piebald'
}

// Note that the order doesn't matter due to the property names
let { name, color, height } = gerryStats;

console.log(height); //16 hands
```

If we want to rename the variable something other than the property name we can  do it using a colon.

```javascript
let gerryStats = {
  name: 'Fast Gerry',
  height: '16 hands',
  color: 'Piebald'
}

// Note that the order doesn't matter due to the property names
let { name : horseName, color : horseColor, height: horseHeight } = gerryStats;

console.log(horseHeight); //16 hands
```

## Default Values

If we try to operate on absent values they are undefined, if we need to ensure that there is a value we can add defaults.

```javascript
// A shorter array
let raceFinishers = ['Gary', 'Lenny', 'Karl']

let [firstPlace, secondPlace ,thirdPlace, fourthPlace] = raceFinishers;

console.log(fourthPlace); //Undefined

```

We could rewrite the above like so:

```javascript
// A shorter array
let raceFinishers = ['Gary', 'Lenny', 'Karl']

let [firstPlace = 'A. Winner', secondPlace = 'A. FirstLoser' ,thirdPlace = 'A. ThirdPlace', fourthPlace = 'A. FourthPlace'] = raceFinishers;

console.log(fourthPlace); //A.FourthPlace
```

For objects, we can combine the colon syntax with defaults:

```javascript
let gerryStats = {
  name: 'Fast Gerry'
}

// Note that the order doesn't matter due to the property names
let { name : horseName = 'frank', color : horseColor = 'black', height: horseHeight = '13 hands' } = gerryStats;

console.log(horseHeight); //13 hands
```

## Reassigning Names

We can reassign the values of variables easily using destructuring

```javascript
let horseName = 'Fancy John Jones';
let jockeyName = 'Dale Earnhardt Jr Jr';

// We need to swap these around.
[jockeyName, horseName] = [horseName, jockeyName];

console.log(`The horse was named ${horseName}, the jockey: ${jockeyName}`); 
//"The horse was named Dale Earnhardt Jr Jr, the jockey: Fancy John Jones"
```

