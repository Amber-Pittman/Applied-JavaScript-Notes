# Introduction to the DOM

## A. What is the DOM?
  1. It is the Document Object Model
  2. An object representation of the HTML elements of a webpage. 
  3. It is *NOT* the HTML page itself. 
  4. The DOM is an Application Programming Interface (API). In our case, the DOM is a bridge between Content and the browser. Content -- DOM --> Browser
## B. What the DOM is *NOT*:
  1. JavaScript
  2. HTML or CSS
  3. Static - "Static" doesn't change or do anything
## C. What the DOM *IS*:
  1. Language-Neutral API - This means JavaScript is not the *only* language that can actually manipulate it
  2. Tree-like structure representing your content, structure, and style
  3. Dynamic - meaning, if we change it live, it changes right before our eyes. 
## D. Document (Node Element)

## E. Code
  1. Go into browser developer tools
  2. "Elements" show you how the page is built out
    ** Go to the `<h1>` tag
    ** Type "This is the DOM!"
    ** Click off or away from the `<h1>` tag
    ** It updates with the new text
    ** This is *not* permanent! It's only visible on your own browser. This is great for experimenting!
  3. Go to "Console"