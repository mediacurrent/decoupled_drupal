# Modules

As we create larger and more complex applications we will need to split our code into sensible contained files. We call these 'modules' and they typically  contain a class or library of functions. 

Modules can be loaded into each other and give access to the functionality within the files they are imported into.

```javascript
// nameJockey.js

export function nameJockey( name ) {
  return `This jockey is named ${name}`
}
```

```javascript
// otherFile.js
// Loaded by path relative to location of otherFile.js
import {nameJockey} from './nameJockey.js';

nameJockey('Gerald McJockey'); // Gerald McJockey
```

### import/export

### default

### named

