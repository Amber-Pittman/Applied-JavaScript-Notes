## Introduction to the DOM

### A. What is the DOM?
  1. It is the Document Object Model
  2. An object representation of the HTML elements of a webpage. 
  3. It is *NOT* the HTML page itself. 
  4. The DOM is an Application Programming Interface (API). In our case, the DOM is a bridge between Content and the browser. Content -- DOM --> Browser
### B. What the DOM is *NOT*:
  1. JavaScript
  2. HTML or CSS
  3. Static - "Static" doesn't change or do anything
### C. What the DOM *IS*:
  1. Language-Neutral API - This means JavaScript is not the *only* language that can actually manipulate it
  2. Tree-like structure representing your content, structure, and style
  3. Dynamic - meaning, if we change it live, it changes right before our eyes. 
### D. Document (Node Element)

### E. Code
  1. Go to https://lambdaschool.com/ and get into browser developer tools
  2. "Elements" show you how the page is built out
    <ul><li> Go to the `<h1>` tag </li>
    <li> Type "This is the DOM!"</li>
    <li> Click off or away from the `<h1>` tag </li>
    <li> It updates with the new text </li>
    <li> This is *not* permanent! It's only visible on your own browser. This is great for experimenting! </li></ul>
  3. Go to "Console"
    <ul><li> Type in `console.log(document)` </li>
    <li> Click on the arrow next to `#document` </li>
    <li> You'll see all the Elements of the Dom tree </li></ul>

## DOM Selectors

### A. In order to access the DOM, in "console," we use `document` as our base.

1. `document.getElementsByTagName("div");` Grabs all the divs on the page
    <ul><li> You'll get an HTMLCollection: 
    <img src="images/All-Divs-DOM-I.PNG"></li></ul>
2. If you type in `document.getElementsByClassName("navigation-item");`, you will get an HTMLCollection of just the navigation-item class
    <ul><li> HTMLCollection of the class "navigation-item" </li>
    <img src="images/Nav-Item-DOM-I.PNG"></ul>
3. `document.getElementById("Pick-Track");` This version only has 1 element because it is targeting an ID
    <ul><li> Get Element by ID, "Pick-Track" </li>
    <img src="images/Element-ID-DOM-I.PNG"></ul>
4. `document.querySelector("div");` 
    <ul><li> Query Selector takes 1 string, no matter how many are available.</li>
    <li> Basically anything we can select by CSS</li>
    <img src="images/Query-Selector-DOM-I.PNG"></ul>
5. `document.querySelectorAll("navigation-item");`
    <ul><li>Returns a node list back</li>
    <li> Almost identical to an HTMLCollection</li>
    <li> Click on arrow next to NodeList to explore more</li>
    <img src="images/Query-Selector-All-DOM-I.PNG"></ul>

### B. Difference between HTMLCollection and NodeList

1. Similarities
    <ul><li>Both look like arrays</li>
    <li>Zero-based Index</li>
    <li>List of Items</li>
    <li>Both have length property</li>
    <li>Shallow Copied</li></ul>
2. Differences
    <ul><li>NodeLists can use the forEach() method, but HTMLCollection does NOT have that function.</li>
    <li>NodeLists provide more built-in methods</li>
    <li>HTMLCollection is faster in performance because there are NO built-in methods</li></ul>

## Review MDN Resources

1. [MDN DOM page](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)
2. [HTMLCollection Page] (https://developer.mozilla.org/en-US/docs/Web/API/HTMLCollection)