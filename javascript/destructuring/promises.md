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
  }, 3000);
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

Async/await gives us a different syntax for dealing with promises. The async keyword is a promise based behavior. You can see below that when we declared our promise above, we had to declare the resolve, the async return is the resolve so below we return true vs. `return Promise.resolve(true)` so we are avoiding the need to explicitly configure promise chains.

```javascript
async function aysnc1() {
  setTimeout(function(){ 
    //return Promise.resolve(true);
    return true;
  }, 3000);

}

aysnc1().then(console.log('done!')); // done
```

The wait keyword makes JavaScript wait until that promise settles and returns its result.

```javascript
// wait ms milliseconds
function wait(ms) {
  return new Promise(r => setTimeout(r, ms));
}

async function hello( time, message) {
  try {
      await wait(time);
      console.log(message);
    } catch(err) {
      alert(err); // TypeError: failed to fetch
  }
}

hello(500, 'one');
```

