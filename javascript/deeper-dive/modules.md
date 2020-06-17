# Modules

As we create larger and more complex applications we will need to split our code into sensible contained files. We call these 'modules' and they typically  contain a class or library of functions. 

Modules can be loaded into each other and give access to the functionality within the files they are imported into.

```javascript
// nameJockey.js

function nameJockey( name ) {
  return `This jockey is named ${name}`
}

let tremendous = true;

export { nameJockey, tremendous }
```

```javascript
// otherFile.js
// Loaded by path relative to location of otherFile.js
import {nameJockey, tremendous} from './nameJockey.js';

nameJockey('Gerald McJockey'); // Gerald McJockey
```

There are two types of exports, named and default. You can have multiple named exports per module but only one default.

```javascript
// named exports

function nameJockey( name ) {
  return `This jockey is named ${name}`
}

let tremendous = true;

export { nameJockey, tremendous }

// default exports

export default function nameJockey( name ) {
  return `This jockey is named ${name}`
}


```

