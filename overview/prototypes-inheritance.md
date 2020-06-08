# Prototypes / Inheritance

When functions are created, javascript adds a prototype property. This prototype object is shared across all instances of the function. This means that if we use the prototype object we can update our function of all instances it is used.

```javascript
function horseInRace() {
  this.name = 'Andrew the fast';
  this.racesEntered = 7;
}

const horse1 = new horseInRace();
horse1.name = 'stewart the steady';

console.log(horse1); // object { name: "stewart the steady", reacesEntered: 7}

horse1.racesWon = 5;

console.log(horse1); // object {name: "stewart the steady", racesEntered: 7, racesWon: 5}

const horse2 = new horseInRace();
console.log(horse2.racesWon); //undefined

```

In the above example, we establish a horseInRace function that contains some default values.  We then create horse1 and assign it some new values, we update the name and give the horse a value for the races won.  When we create horse2 and try to find out its value for racesWon it is undefined. This is where prototypes allow us to update all of the instances of horseInRace.

```javascript
function horseInRace() {
  this.name = 'Andrew the fast';
  this.racesEntered = 7;
}

// Add to the prototype
horseInRace.prototype.racesWon = 7;

// Create a new horse
const horse1 = new horseInRace();
horse1.name = 'stewart the steady';
horse1.racesWon = 3;

// Create a new horse 
const horse2 = new horseInRace();

console.log(horse1); // Object { name: "stewart the steady", racesEntered: 7, racesWon: 3 }
console.log(horse2); // Object { name: "Andrew the fast", racesEntered: 7, racesWon: 7 }

```

#### Inheritance

If we have a constructor, or function that we want to use to create other similar objects, we could copy the code, or we could take advantage of inheritance and do less work. 

```javascript
function horseInRace(name, racesEntered, racesWon) {
  this.name = name;
  this.racesEntered = racesEntered;
  this.racesWon = racesWon;
}
```

Now we want to have a similar class for our jockeys that will have some additional properties. Our jockey will include bib color and home town.

```javascript
function jockeyInRace(name, racesEntered, racesWon, bibColor, homeTown) {
  horseInRace.call(this, name, racesEntered, racesWon);
  this.bibColor = bibColor;
  this.homeTown = homeTown;
}

let steve = new jockeyInRace( 'Steve', 7, 7, 'Red', 'Orange Park');

console.log( steve ); // Object { bibColor: "Red", homeTown: "Orange Park", name: "Steve", racesEntered: 7,racesWon: 7 }
```

Using the call\(\) function allows us to call a function defined elsewhere within the current context.

We also need to make sure we inherit any methods that the original prototype had, so that we can use the data for the jockey in the same way we would for the horse.

```javascript
function horseInRace(name, racesEntered, racesWon) {
  this.name = name;
  this.racesEntered = racesEntered;
  this.racesWon = racesWon;
}

horseInRace.prototype.winPercent = function() {
  console.log(this.name + ' has won '+ (this.racesWon / this.racesEntered) *100 +'% of their races');
};

let gary = new horseInRace('gary', 5, 4);
gary.winPercent(); //gary has won 80% of their races.

```

Above we have added a method to our constructor. If we tried to call this from on our jockey it would error.

```javascript
function horseInRace(name, racesEntered, racesWon) {
  this.name = name;
  this.racesEntered = racesEntered;
  this.racesWon = racesWon;
}

horseInRace.prototype.winPercent = function() {
  console.log(this.name + ' has won '+ (this.racesWon / this.racesEntered) *100 +'% of their races');
};

let gary = new horseInRace('gary', 5, 4);
gary.winPercent()); //gary has won 80% of their races. 

function jockeyInRace(name, racesEntered, racesWon, bibColor, homeTown) {
  horseInRace.call(this, name, racesEntered, racesWon);
  this.bibColor = bibColor;
  this.homeTown = homeTown;
}

let steve = new jockeyInRace( 'Steve', 7, 7, 'Red', 'Orange Park');

console.log( steve ); // Object { bibColor: "Red", homeTown: "Orange Park", name: "Steve", racesEntered: 7,racesWon: 7 }
steve.winPercentage(); // Uncaught TypeError: steve.winPercentage is not a function 
```

This is because our jockey constructor doesn't contain a reference to the methods of the horseInRace prototype. We need to establish that relationship so we have updated the jockeyInRace prototype to be equal to a horseInRace prototype. We are also resetting the constructor to be jockeyInRace so that we are inheriting and not cloning.

```javascript
function horseInRace(name, racesEntered, racesWon) {
  this.name = name;
  this.racesEntered = racesEntered;
  this.racesWon = racesWon;
}

horseInRace.prototype.winPercent = function() {
  console.log(this.name + ' has won '+ (this.racesWon / this.racesEntered) *100 +'% of their races');
};

let gary = new horseInRace('gary', 5, 4);
gary.winPercent();

function jockeyInRace(name, racesEntered, racesWon, bibColor, homeTown) {
  horseInRace.call(this, name, racesEntered, racesWon);
  this.bibColor = bibColor;
  this.homeTown = homeTown;
}

jockeyInRace.prototype = Object.create(horseInRace.prototype);
jockeyInRace.prototype.constructor = jockeyInRace;

let steve = new jockeyInRace( 'Steve', 7, 7, 'Red', 'Orange Park');

console.log( steve ); // homeTown: "Orange Park", name: "Steve", racesEntered: 7, racesWon: 7, winPercent: function () { console.log(this.name + ' has won ' + this.racesWon / this.racesEntered * 100 + '% of their races');
steve.winPercent(); // "Steve has won 100% of their races"
```

