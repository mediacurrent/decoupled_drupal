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



## Default Values

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

