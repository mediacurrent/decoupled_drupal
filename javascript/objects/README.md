# Fundamentals

## Objects

As discussed in the [types](../overview/types-data-types.md#object) section, objects are entities with properties that define their characteristics.

```javascript
let horse = {
  color: 'piebald',
  height: '13 hands',
  speed: 'very fast',
  temperament: 'fiesty'
}
```

We can consider the properties as variables attached to the object, accessed like this:

```javascript
// dot syntax
console.log(horse.color); // piebald;

// bracket notation
console.log(horse['color']); //piebald;
```

Objects are sometimes known as associative arrays, since each property is associated with a string value that can be used to access the properties. Any property name that is not a valid identifier ie starts with a symbol, or a number can only be accessed with bracket notation.

```javascript
horse['color'] = 'piebald';
```

We can create objects in serval ways. This technique is called an initializer:

```javascript
let horse = {
  color: 'piebald',
  height: '13 hands',
  speed: 'very fast',
  temperment: 'fiesty',
  'string identifier': 'yes',
  7: 'number identifier'
}
```

We can use a constructor function:

```javascript
function race(type, location, climate) {
  this.type = type;
  this.location = location;
  this.climate = climate;
}

var myRace = new race('flat', 'florida', 'hot and humid');
```

We can also use the object.create method:

```javascript
let horse = {
  color: 'piebald',
  height: '13 hands',
  speed: 'very fast',
  temperament: 'fiesty'
}

let andrewTheHorse = Object.create(horse);
console.log(andrewTheHorse.temperament) // fiesty

let gregoryTheHorse = Object.create(horse);
gregoryTheHorse.temperament = 'placid';
console.log(gregoryTheHorse.temperament) // placid
```

Using this method, you can see we are [inheriting](../overview/prototypes-inheritance.md) properties from the horse prototype.

Objects can also have properties that are methods. Methods are defined the same way functions are except that they have to be assigned as a property.

```javascript
let horse = {
  color: 'piebald',
  height: '13 hands',
  speed: 'very fast',
  temperment: 'fiesty',
  // One method definition technique
  racesNotFinished: function(racesStarted, racesFinished) {
      return racesStarted - racesFinished;
    },
  // Another valid definition technique.
  raceWinPercentage(racesEntered, racesWon) {
    return (racesWon / racesEntered)*100;
    }
  };

console.log(horse.raceWinPercentage(5, 4)); //80
```

We can also add a function and make that a method on the object:

```javascript
function race(type, location, climate) {
  this.type = type;
  this.location = location;
  this.climate = climate;
  this.aboveSeaLevel = aboveSeaLevel;
}

// One method definition technique
function aboveSeaLevel(seaLevel, altitude) {
    console.log(altitude - seaLevel);
 };

let myRace = new race('flat', 'florida', 'hot and humid');

myRace.aboveSeaLevel(0, 200); // 200
```

