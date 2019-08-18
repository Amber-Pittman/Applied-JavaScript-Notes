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

