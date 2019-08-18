## Components I

### Anatomy of a Component

1. Component - a part of element of a larger whole
2. They are single, modular pieces of code
3. Usually made up of all 3 "languages" - HTML, CSS, and JavaScript
4. Components are Reusable. We want to keep our code DRY
5. Usually, components can stand alone

### Component Creator Functions

1. How do you create a brand new component in JavaScript?

`document.createElement` creates a brand new element and is going to live in memory.

For example, you want to create a button in JavaScript. 

`document.createElement("button"); // creates the button`

You'll need to assign it a variable. Change it to this:

```
let button = document.createElement("button");
console.log(button); // shows <button></button> in the console of dev tools
```

Now you want to add text to the button so your users know what to do with it. 

```
let button = document.createElement("button");
console.log(button); // shows <button></button> in the console of dev tools

button.textContent = "This is a button component";
console.log(button); // shows <button>This is a button component</button> in console
```

The next logical step is adding a class to the button.

```
let button = document.createElement("button");
console.log(button); // shows <button></button> in the console of dev tools

button.textContent = "This is a button component";
console.log(button); // shows <button>This is a button component</button> in console

button.classList.add("btn");
button.classList.add("lg-btn"); // Adds both classes to button tags in console
```

2. How to add the the element (the button) to the page without using HTML

#### Grab the parent from the HTML and put it in the JavaScript file
In this case, the parent would be the container div. 

```
let button = document.createElement("button");
console.log(button); 

button.textContent = "This is a button component";
console.log(button); 

button.classList.add("btn");
button.classList.add("lg-btn"); 

let container = document.querySelector(".container") // Grabs parent from HTML
container.appendChild(button); // Adds it to the JS element, button
```

3. Add functionality to your button

```
let button = document.createElement("button");
console.log(button); 

button.textContent = "This is a button component";
console.log(button); 

button.classList.add("btn");
button.classList.add("lg-btn"); 
button.addEventListener("click", (event) => {             // Here's the functionality
    console.log(`The button clicked says: ${event.target.textContent}`)
})

let container = document.querySelector(".container") 
container.appendChild(button); 
```

4. What if you wanted more than one button?
The previous code isn't ideal because it won't follow the DRY method if you repeat it with a new button 
variable like `let button 2`. Instead, create a function and put the previous code inside it.

```
function buttonCreator() {
    let button = document.createElement("button");
    console.log(button); 
    
    button.textContent = "This is a button component";
    console.log(button); 
    
    button.classList.add("btn");
    button.classList.add("lg-btn"); 
    button.addEventListener("click", (event) => {             
      console.log(`The button clicked says: ${event.target.textContent}`)
    });
    
    return button; // Return gets the data out of the function
}

const button = buttonCreator(); // calls the function
console.log("The product of the buttonCreator function is ", button);
```

By making the buttonCreator function a variable, it grabs hold of what the button returns. At this point, it's 
still not visible on screen. Shows up in console only. To add it to the screen, you need to add it to the container.

```
function buttonCreator() {
    let button = document.createElement("button");
    console.log(button); 
    
    button.textContent = "This is a button component";
    console.log(button); 
    
    button.classList.add("btn");
    button.classList.add("lg-btn"); 
    button.addEventListener("click", (event) => {             
      console.log(`The button clicked says: ${event.target.textContent}`)
    });
    
    return button; // Return gets the data out of the function
}

const button = buttonCreator(); 
console.log("The product of the buttonCreator function is ", button);

let container = document.querySelector(".container");
container.appendChild(button); // Adds it to the container
```

This is now DRY code. You can now add extra buttons. To add more buttons, go back to the buttonCreator() variable.

```
function buttonCreator() {
    let button = document.createElement("button");
    console.log(button); 
    
    button.textContent = "This is a button component";
    console.log(button); 
    
    button.classList.add("btn");
    button.classList.add("lg-btn"); 
    button.addEventListener("click", (event) => {             
      console.log(`The button clicked says: ${event.target.textContent}`)
    });
    
    return button; // Return gets the data out of the function
}

const button = buttonCreator(); 
const button2 = buttonCreator(); // calls function again & creates a brand new button
console.log("The product of the buttonCreator function is ", button);

let container = document.querySelector(".container");
container.appendChild(button); 
```

After adding your new button, you then want to go back down to the end of the code. You'll need to add the new button 
visibly to the page. 

```
function buttonCreator() {
    let button = document.createElement("button");
    console.log(button); 
    
    button.textContent = "This is a button component";
    console.log(button); 
    
    button.classList.add("btn");
    button.classList.add("lg-btn"); 
    button.addEventListener("click", (event) => {             
      console.log(`The button clicked says: ${event.target.textContent}`)
    });
    
    return button; // Return gets the data out of the function
}

const button = buttonCreator(); 
const button2 = buttonCreator(); // calls function again & creates a brand new button
console.log("The product of the buttonCreator function is ", button);

let container = document.querySelector(".container");
container.appendChild(button); 
container.appendChild(button2); // Adds new button to the visible page
```

Additionally, you could skip the `container.appendChild(button);` way. You could use `container.appendChild(buttonCreator());` 
to handle all your button variables.

```
function buttonCreator() {
    let button = document.createElement("button");
    console.log(button); 
    
    button.textContent = "This is a button component";
    console.log(button); 
    
    button.classList.add("btn");
    button.classList.add("lg-btn"); 
    button.addEventListener("click", (event) => {             
      console.log(`The button clicked says: ${event.target.textContent}`)
    });
    
    return button; // Return gets the data out of the function
}

const button = buttonCreator(); 
const button2 = buttonCreator(); 
const button3 = buttonCreator(); // Added button3-4 for example purposes
const button4 = buttonCreator(); 
console.log("The product of the buttonCreator function is ", button);

let container = document.querySelector(".container");
container.appendChild(buttonCreator()); // Should make all buttons visible without extra code
```

5. How to make elements (the buttons) more dynamic. 
For example, you probably want the button text to be different for each one. 

```
function buttonCreator(text) {  // We added a parameter. In this case, text, so we can change the button text
    let button = document.createElement("button");
    console.log(button); 
    
    button.textContent = text; // We replaced "This is a button component" with the parameter of text
    console.log(button); 
    
    button.classList.add("btn");
    button.classList.add("lg-btn"); 
    button.addEventListener("click", (event) => {             
      console.log(`The button clicked says: ${event.target.textContent}`)
    });
    
    return button; // Return gets the data out of the function
}

// Since adding text to the parameters of buttonCreator, we'll need to provide that for the elements as well
const button = buttonCreator("This is the 1st button component"); 
const button2 = buttonCreator("This is a 2nd button component"); 
const button3 = buttonCreator("This is a 3rd button component");
const button4 = buttonCreator("This is a 4th button component"); 
console.log("The product of the buttonCreator function is ", button);

let container = document.querySelector(".container");
container.appendChild(buttonCreator()); // Should make all buttons visible without extra code
```
The `function buttonCreator` is now reusable and dynamic. :) 

### Creating Components from Array Data

Most of the time when we get data back, we don't know what's in that data. We expect it to be formed a certain way that should
be constant in how data is formed.

Sometimes, we want to build and display a component for each item in that data. This is most likely an array. We want to
do this dynamically. 

```
const fakeData = [  // array of data
    "Button One",
    "Button Two",
    "Button Three",
    "Button Four"
]
```

1. How do we access this data using our previous code? You will update the button variables outside the function. 

```
const fakeData = [
    "Button One",
    "Button Two",
    "Button Three",
    "Button Four"
]

function buttonCreator(text) {  
    let button = document.createElement("button");
    console.log(button); 
    
    button.textContent = text; 
    console.log(button); 
    
    button.classList.add("btn");
    button.classList.add("lg-btn"); 
    button.addEventListener("click", (event) => {             
      console.log(`The button clicked says: ${event.target.textContent}`)
    });
    
    return button; // Return gets the data out of the function
}


const button = buttonCreator(fakeData[0]);  // Replaces the original text 
const button2 = buttonCreator(fakeData[1]); 
const button3 = buttonCreator(fakeData[2]);
const button4 = buttonCreator(fakeData[3]);
console.log("The product of the buttonCreator function is ", button);

let container = document.querySelector(".container");
container.appendChild(buttonCreator()); // Should make all buttons visible without extra code. 

/* If not, use this instead:
container.appendChild(button);
container.appendChild(button2);
container.appendChild(button3);
container.appendChild(button4); */
```

What if "Button Five" gets added into the array later? Although it is in the array, it will not display. It needs to 
be appended. You could update the `const button` section and the `container.appendChild` section. It is a tedious process.

What if the array index 0-3 were removed in the array but the rest of the code still acknowledges the presence of them? 
Most often it will break the code. "Text content of undefined" in console. 

So right now, in this aspect, our code is not DRY. We're not being flexible enough so that we can dynamically create
components based on the data that we have. 

There are a couple of different ways we can achieve dynamic code. You can use a `for loop`, `.forEach()`, or `.map()`.

<ul><li>Using a for loop:</li>

```
const fakeData = [
    "Button One",
    "Button Two",
    "Button Three",
    "Button Four"
]

function buttonCreator(text) {  
    let button = document.createElement("button");
    console.log(button); 
    
    button.textContent = text; 
    console.log(button); 
    
    button.classList.add("btn");
    button.classList.add("lg-btn"); 
    button.addEventListener("click", (event) => {             
      console.log(`The button clicked says: ${event.target.textContent}`)
    });
    
    return button; // Return gets the data out of the function
}


const button = buttonCreator(fakeData[0]);  
const button2 = buttonCreator(fakeData[1]); 
const button3 = buttonCreator(fakeData[2]);
const button4 = buttonCreator(fakeData[3]);
console.log("The product of the buttonCreator function is ", button);

let container = document.querySelector(".container");

for (let i = 0; i < fakeData.length; i++) {   // Add the for loop
    let button = buttonCreator(fakeData[i]);
    console.log(button);
}

container.appendChild(button);
```

<li>An Array Method</li>

```
const fakeData = [
    "Button One",
    "Button Two",
    "Button Three",
    "Button Four"
]

function buttonCreator(text) {  
    let button = document.createElement("button");
    console.log(button); 
    
    button.textContent = text; 
    console.log(button); 
    
    button.classList.add("btn");
    button.classList.add("lg-btn"); 
    button.addEventListener("click", (event) => {             
      console.log(`The button clicked says: ${event.target.textContent}`)
    });
    
    return button; // Return gets the data out of the function
}


const button = buttonCreator(fakeData[0]);  
const button2 = buttonCreator(fakeData[1]); 
const button3 = buttonCreator(fakeData[2]);
const button4 = buttonCreator(fakeData[3]);
console.log("The product of the buttonCreator function is ", button);

let container = document.querySelector(".container");

fakeData.forEach((item) => {
    let button = buttonCreator(item); // Don't have to specify array index here
    container.appendChild(button); // Puts this inside the forEach()
}) //This is really good if we just want to iterate over the data and add it to our DOM right away; INSTANT

```

<li>Mapping</li></ul>

```
const fakeData = [
    "Button One",
    "Button Two",
    "Button Three",
    "Button Four"
]

function buttonCreator(text) {  
    let button = document.createElement("button");
    console.log(button); 
    
    button.textContent = text; 
    console.log(button); 
    
    button.classList.add("btn");
    button.classList.add("lg-btn"); 
    button.addEventListener("click", (event) => {             
      console.log(`The button clicked says: ${event.target.textContent}`)
    });
    
    return button; // Return gets the data out of the function
}


const button = buttonCreator(fakeData[0]);  
const button2 = buttonCreator(fakeData[1]); 
const button3 = buttonCreator(fakeData[2]);
const button4 = buttonCreator(fakeData[3]);
console.log("The product of the buttonCreator function is ", button);

let container = document.querySelector(".container");

let buttonsArray = fakeData.map((item) => { 
    // Map returns new array with the new items after being manipulated by the cb function
    let button = buttonCreator(item); 
    return button; //Map requires the return ALWAYS
});

console.log("Here are the buttons", buttonsArray);
 /* Now we have an array full of buttons using .map(). The buttons are not visible on the screen yet. Will 
come back to this in later modules. */

```


