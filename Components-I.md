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

