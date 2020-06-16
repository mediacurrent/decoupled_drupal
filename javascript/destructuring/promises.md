# Promises

A promise allows code to take the time it needs to run and make the result available when it is ready. This is called asynchronous.

```javascript
let promise = new Promise(function(resolve, reject) {
  // executor (the producing code, "singer")
});
```

A promise is an object which can be returned synchronously from this asynchronous function. It will be in one of 3 possible states:

* **Fulfilled**
* **Rejected**
* **Pending**

A promise is **settled** if it’s not pending \(it has been resolved or rejected\). Once settled, a promise can not be resettled. Calling `resolve()` or `reject()` again will have no effect because promise is immutable.

Below we have defined a promise and used a settimeout to simulate waiting on results. We are doing a basic comparison on two values, and either resolving or rejecting based on the result.

```javascript
let horseChecking = new Promise(function(resolve, reject) {
  const horseName = 'Juanita';
  const horseNameOnPassport = 'Juanita';

  setTimeout(function() { 
    if(horseName  === horseNameOnPassport) {
      resolve();
    } else {
      reject();
    }
  }, 3000);
});

horseChecking
  .then(function () { 
    console.log('They Matched!');
   })
  .catch(function () {
    console.log('An error occured');
  });
```

You can see that the action that occurs when resolve occurs happens in the then section

```javascript
  .then(function () { 
    console.log('They Matched!');
   })
```

We can chain items togethers like this, where our then's occur in order once each completes:

```javascript
let horseChecking = new Promise(function(resolve, reject) {
  const horseName = 'Juanita';
  const horseNameOnPassport = 'Juanita';

  setTimeout(function(){ 
    if(horseName  === horseNameOnPassport) {
      resolve();
    } else {
      reject();
    }
  }, 2000);
});

horseChecking
  .then(function () { 
    console.log('They Matched!');
   })
  .then(function () { 
    console.log('They Still Matched!');
   })
  .then(function () { 
    console.log('They Stilllllllll Matched!');
   })
  .catch(function () {
    console.log('An error occured');
  });
```

Because these are based on one promise, the chain will immediately cascade once the initial promise resolves. If we wanted each `then` to be dependent on another asynchronous call, we would need to create a new promise each time. Modifying our code above would look like:

```javascript
horseChecking
  .then(function () { 
    console.log('They Matched!');
   })
  .then(function () { 
    return new Promise(function(resolve, reject) {
     setTimeout(function(){ 
       resolve();
       console.log('They Still Matched!');
    }, 2000);
    })
   })
  .then(function () { 
    return new Promise(function(resolve, reject) {
     setTimeout(function(){ 
       resolve();
       console.log('They Stilllllllll Matched!');
    }, 2000);
    })
   })
  .catch(function () {
    console.log('An error occured');
  });
```

Async/await provides the same functionality as promises but with a different syntax that is generally considered cleaner. To make a function asynchronous, add the `async` keyword before it. The `await` keyword makes JavaScript wait until the promise settles and returns its result. This enables us to make variables and other items dependent on asynchronous data. The `await` keyword can only be used inside an `async` function.

```javascript
const horseName = 'Juanita';

function getHorseData() {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve('Juanita');
    }, 2000);
  });
}

async function checkHorseName(name) {
  const nameOnPassport = await getHorseData();
  if (name  === nameOnPassport) {
    console.log('They Matched!');
  } else {
    console.log('An error occured');
  }
}

checkHorseName(horseName);
```

