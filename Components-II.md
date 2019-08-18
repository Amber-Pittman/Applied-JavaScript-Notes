## JavaScript Promises

### 1. Promises and Asynchronous Code

#### A. Asynchronous (async) Code
<ul>
<li>Makes it possible for a JavaScript Engine to do 2 things at the same time... or "asynchronously"</li>
<li>We can use async code to allow the browser to keep executing code while something else is happening (usually a call to an external API for data).</li>
<li>When we use this technique, we create a helper object, called a "Promise," to inform the browser that the 2nd async task has finished.</li>
</ul>

#### B. Promises
<ul>
<li>A promise is simply an object with a few properties.</li>
<li>When we want to run some async code, we create a new Promise, and use that Promise to inform the JavaScript engine that the async function has finished.</li>
<li>When we instantiate a new Promise with the `new` keyword,, w pass in a callback function that receives a `resolve()` function and a `reject()` function.</li>
<li>If the async function finishes and was successful, we call the `resolve()` function. If it were unsuccessful, we call the `reject()` function.</li>
<li>When a Promise is resolved or rejected, we use the Promise object's methods, `.then()` or `.catch()` to tell the JavaScript engine what to do next.</li>
</ul>

#### C. The `.then()` and `.catch()` Methods
<ul>
<li>The `.then()` and the `.catch()` are both methods on the Promise object that receives a callback function as an argument.</li>
<li>When our async function finishes running, that callback function is executed.</li>
</ul>

### 2. Async Function Example

```
const asyncFunction = () => {
    return new Promise((resolve, reject) => {
        // Perform some async action
    });
};
```

The asyncFunction here creates and returns a new promise. As you can see, we are passing in a callback function where we are 
instantiating this new Promise with the `new` keyword. That callback function is taking in 2 arguments - a resolve function and a reject
function. Then, inside the Promise, we perform some asynchronous action.

This means that whatever we call this function, we can use `.then()` or `.catch()` methods to tell the JavaScript engine what we want
to do now that the Promise has been resolved or rejected. 

```
const asyncFunction = () => {
    return new Promise((resolve, reject) => {
        // Perform some async action
    });
};


asyncFunction() {
    .then(() => {
        console.log("Async stuff finished.");
    });
    .catch(() => {
        console.log("Async stuff rejected.");
    });
}
```

The syntax here is what we call `Chaining Methods`. So, `.then()` is chained off the asyncFunction call. And `.catch()` is chained off 
the `.then()` call. 

### 3. In the next scenario, the asynchronous function finished successfully.

```
const asyncFunction = () => {
    return new Promise((resolve, reject) => {
        if (asyncFinishesSuccessfully) {
            resolve(dataObject);
        }
    });
};


asyncFunction() {
    .then(dataPassedFromResolve => {
        console.log("The data passed from resolve.");
    });
    .catch(() => {
        console.log("Async stuff rejected.");
    });
}
```

If we call `resolve()` and pass in something, the `.then()` function gets called with that data passed into it. 

### 4. Now we have an asynchronous function finished unsuccessfully.

Now we have a situation where the async call may not have finished successfully or the API we sent the call out to sent 
back an error message. We then would use and invoke the `.reject()` method and pass in that error message or error
Object to the `.catch()` function. 

If we call `.reject()` and pass in something, the `.catch()` function gets called with that data passed into it.

```
const asyncFunction = () => {
    return new Promise((resolve, reject) => {
        if (asyncFinishesSuccessfully) {
            resolve(dataObject);
        } else {
            reject(errorMessage);
        }
    });
};


asyncFunction() {
    .then(dataPassedFromResolve => {
        console.log("The data passed from resolve.");
    });
    .catch(errorPassedFromReject => {
        console.log("Error message passed from reject");
    });
}
```

## API Calls

Keep in mind that when we make API calls, we usually invoke a function that, under the "hood", 
will return a promise and handle calling `resolve()` or `reject()` for us.

In these cases, we don't have to create a new Promise in our code. However, we will still 
have access to the `.then()` and `.catch()` functions.

For example, here is a call to the Star Wars API. To make this API call, we're using a 3rd party
library called Axios. Axios has a function called `.get()`. The `.get()` function is going to create
a new Promise and handle calling `.resolve()` or `.reject()`. We can chain our `.then()` and 
`.catch()` functions off of the `.get()` function call.

When we make this API call, the call goes out to the Star Wars API. 
<ul>
<li>if that call comes back successfully, we will go into our `.then()` function and receive some
response from the API. Then we have to handle that data/response call.</li>
<li>If the API call comes back unsuccessfully, and the API sends back an error, then we go into the
`.catch()` method. There we have to handle that error we received back from the API.</li>
</ul>

```
axios.get("https://swapi.co/api/people") {
    .then(response => {
        // Do something with the datawe are getting in response to the API call we just made
        console.log("response");
    })
    .catch(err => {
        // Handle the error that we received from the API
        console.log("response");
    });
}
```

### Chaining `.then()`

```
let time = 0;
const timeMachine = () => {
    return new Promise ((resolve, reject) => {
        setTimeout(() => {
            resolve((time += 1000)); // 1st parameter
        }, 1000); // 1000 is the 2nd parameter
    });
};

timeMachine().then(newTime => {
    console.log(newTime); // Outputs 1000
});
```

The `setTimeout()` function is an async function that is often used to kind of fake API calls that could
take 1 second (written as 1000 in ms as above). The 2nd parameter (1000) is where we determine the amount of
time it takes. After 1000ms (or 1 second), it will run the resolve function. Then we can invoke our 
timeMachine() function and chain our `.then()` function off the function call (`timeMachine()`).

When the `.resolve()` runs, the callback function inside the `.then()` will get called. It will console.log
the time. We will see that it outputs 1000.

You can chain another `.then()` to the function call (timeMachine) off of the first `.then()`. The new one
will take in a new string `.then(newString)` and it's going to console.log a new string that gets passed
in. 

How this works: When we resolve this Promise, we go into the first `.then`, we receive the `(time += 1000)` 
value in `newTime` then return out of the first `.then`. We will jump into the next `.then`. The two `.then`'s
happen synchronously (in order), line by line, top to bottom, left to right.

Since the second `.then` is expecting a string, we need to update the first one. We will create a const variable
of time in seconds. 

```
let time = 0;
const timeMachine = () => {
    return new Promise ((resolve, reject) => {
        setTimeout(() => {
            resolve((time += 1000)); // 1st parameter
        }, 1000); // 1000 is the 2nd parameter
    });
};

timeMachine() {
    .then(newTime => {
        const myTime = newTime/1000; //divided by No. seconds have passed
        return `${myTime} seconds have passed`;
    });
    .then(newString => {
        console.log(newString);
    });
};

```

Why would we want to chain a new `.then`? Sometimes we want to do something with our data before we move to do
something with our data before we move that data along and move it back to part of our applications. 


### Chaining `.catch()`

The `.catch()` function will only run if we invoke the `.reject()` function inside the Promise. The
`timeMachine` variable is going to take in some amount of time and we're going to tell our `setTimeout()` to
run for that amount of time (replaces the 1000 in teh 2nd parameter of setTimeout).

```
const timeMachine = time => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (time > 1000) {
                resolve(time);
            } else {
                reject("Not enough time passed in.");
            }
        }, time); // remember this is the 2nd param of setTimeout
    });
};

timeMachine(1000) {  //Test out 2500 and 990 as well here
    .then(newTime => {
        const myTime = newTime/1000;
        console.log(`${myTime} seconds have passed`);
    });
    .catch(error => {
        console.log(err);
    });
};
```

### Final Notes
1. A Promise is a promise from the Object that will let us know when it has completed (or errored) what we have asked it to do.
2. A Promise can exist in 1 of 3 States:
<ul>
<li>Pending - a state where the promise is neither rejected nor fulfilled. This is the state it is in when we first call it.</li>
<li>Fulfilled - a state where "all is well" and a resolved value can be used by our code.</li>
<li>Rejected - state where "something went wrong" and there is an error that needs to be dealt with.</li>
</ul>

3. If the Promise succeeds, it will return the value as a parameter into a callback passed into the `.then()`. If the promise fails, the callback passes into the `.catch()`, runs and takes an error as its argument. 