# Dom II

## Event Listeners

Read about [DOM Events](https://developer.mozilla.org/en-US/docs/Web/Events) from MDN. 

You'll also want to know about [JavaScript Events](https://developer.mozilla.org/en-US/docs/Web/API/Event), especially [Event Properties](https://developer.mozilla.org/en-US/docs/Web/API/Event#Properties). 



### Mouse Event Example
```
const workBtn = document.getElementById("work-btn");
console.log(workBtn);

workBtn.addEventListener("click", function(event) { // `function` is a callback & `event` is an object
    console.log("I was clicked!");
});
```

```
const firstName = document.querySelector(".first-name");
firstName.addEventListener("click", function(event) {
    console.log(`The mouse clicked and this is my event: ${event}`); 
    // Prints "The mouse clicked and this is my event: [object MouseEvent]"
});
```


### Keyboard Event Example

```
const firstName = document.querySelector(".first-name");
firstName.addEventListener("keydown", function(event) {
    console.log(`A key was pressed down! This is the event: ${event}`);
    // Prints "A key was pressed down! This is the event: [object KeyboardEvent]"
});
```

To specify *which* key was pressed, change the above console.log to:

```
console.log(`A key was pressed down! This is the event: ${event.code}`);
// Prints "A key was pressed down! This is the event: key j" (or whatever key was pressed)
```

You can get even clearer messages by using `${event.key}` instead of `${event.code}`. For example, change the last console.log message to this:
```
console.log(`A key was pressed down! This is the event: ${event.key}`);
// Prints "A key was pressed down! This is the event: j"
```


### Event Handlers

Event handlers are actually on the button or HTML element themselves. 

