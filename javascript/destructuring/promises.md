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

We can 

### .then\(\) Chains

### async/await

