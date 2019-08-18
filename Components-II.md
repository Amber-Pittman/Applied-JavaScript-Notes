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