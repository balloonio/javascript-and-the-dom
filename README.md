# JavaScript and the DOM

Learning notes and hand-ons for Udacity course [JavaScript and the DOM](https://www.udacity.com/course/javascript-and-the-dom--ud117).

>*JavaScript is an extremely powerful programming language. One place where its power truly shines is using it to control a web page. Through this course, you'll learn about the Document Object Model (DOM), how it's created, and what capabilities it provides. Then you'll use JavaScript and the DOM to add, delete, or alter page content; control page styling, and respond to user actions.*

<table>
    <tr>
        <th>Course type</th>
        <td>Free</td>
    </tr>
    <tr>
        <th>Timeline</th>
        <td>Approx. 4 Weeks</td>
    </tr>
    <tr>
        <th>Skill level</th>
        <td>Intermediate</td>
    </tr>
</table>

Prerequisites and Requirements - Students should have experience with the following skills:
- building a website with HTML
- styling page elements with CSS (specifically, selecting elements by ID, class, or tag)
- using the JavaScript data types (e.g. strings, arrays, object, functions, etc.)
- looping through data (e.g. the for loop)

These skills are covered in the following courses:

- [HTML and CSS Syntax](https://github.com/bolunzhang/intro-to-html-and-css)
- [Intro to JavaScript](https://www.udacity.com/course/intro-to-javascript--ud803)

Table of Content

- [Lesson 1: The Document Object Model](#lesson-1-the-document-object-model)
  - [Introduction](#introduction)
  - [The DOM](#the-dom)
  - [Selecting Page Elements With CSS Selectors](#selecting-page-elements-with-css-selectors)
  - [Select Page Element By ID](#select-page-element-by-id)
  - [Select Page Elements By Class Or Tag](#select-page-elements-by-class-or-tag)
  - [Nodes, Elements, and Interfaces...Oh My!](#nodes-elements-and-interfacesoh-my)
  - [More Ways To Access Elements](#more-ways-to-access-elements)
  - [Lesson summary](#lesson-summary)

## Lesson 1: The Document Object Model

### Introduction

You'll be learning so many things in this course! Here are the topics for each lesson:

- Lesson 1 - The Document Object Model
- Lesson 2 - Creating Content with JavaScript
- Lesson 3 - Working with Browser Events
- Lesson 4 - Performance

In Lesson 1, we'll take a dive into what the Document Object Model (DOM) is, how it gets created, and how we can access it with JavaScript.

In Lesson 2, you'll learn to interact with page content using JavaScript. You'll use the skills gained from the first lesson to JavaScript and the DOM to update existing page content, create new page content, add new content to the page, programmatically remove page content, and finally how to style page elements.

In Lesson 3, you'll learn about browser events. There is an entire world of thousands of browser events that are happening when you interact with a website. You can't see them directly, but you'll learn about them, how to listen for them, and how to respond when they occur.

In Lesson 4, you'll learn about Performance. It's never too early to start thinking about the performance implications of code. In this course we'll be writing code that can drastically change website (both its content and its looks!), so we need to make sure that the code we write is both functional and efficient.

As you can see, this course is packed with a ton of information! I hope you're excited to begin!

To be successful in this program, there are a number of technologies that you need to know how to use:

- HTML
- CSS
- JavaScript

With JavaScript, though, it's imperative that you understand the basics of the language (variables, data types, loops, etc.). The course is called "JavaScript and the DOM", so JavaScript knowledge is vital for you to succeed.

The following are a few quiz questions to get you back in the mindset of writing JavaScript.

Q1. Which of the following is the correct way to declare a variable in JavaScript? (assume each line is run in isolation)

- [ ] `name: 'Dominique';`
- [x] `const name = 'Miguel';`
- [x] `var name = 'Orvin';`
- [ ] `set(name, 'Kagure');`

Q2. Given `const locations = ['Florida', 'England', 'Malaysia', 'South Africa', 'Fiji', 'China'];`, which of the following correctly access the string `'Malaysia'`?

- [ ] `locations['Malaysia'];`
- [x] `locations[2];`
- [ ] `locations[3];`

Throughout this course, you'll be using lot of fundamental JavaScript skills, so if you're feeling a bit rusty, make sure to brush up on them now before we start diving into this new content.

And speaking of this new content, we're going to be covering some really exciting stuff!

Throughout this course, you'll level up not only your web knowledge, but also your browser and JavaScript knowledge, so get excited!

### The DOM

In this section, we'll look at the Document Object Model - otherwise known as the DOM.

The words "the DOM" are used all over developer documentation sites and tutorials on writing interactive JavaScript code. But what is it? Perhaps you've used even used the DOM and still aren't quite sure what it is. Is it the browser? Is it a special part of JavaScript? ¯\_(ツ)_/¯

#### DOM Explained

[![DOM Explanation By Illya](https://img.youtube.com/vi/gndOFastyus/0.jpg)](https://www.youtube.com/watch?v=gndOFastyus)

To recap the video, the following steps happen:

- HTML is received
- HTML tags are converted to tokens
- tokens are converted to Nodes
- Nodes are converted to the DOM

When you request a website, no matter what backend language is powering that website, it will respond with HTML. The browser receives a stream of HTML. The bytes are run through a complicated (but fully documented) parsing process that determines the different characters (e.g. the start tag character `<`, an attribute like `href`, a closing angle bracket like `>`). After parsing has occurred, a process called tokenization. **Tokenization** takes one character at a time and builds up **tokens**. The tokens are:

- DOCTYPE
- start tag
- end tag
- comment
- character
- end-of-file

Let's take a break for a second. At this state, the browser has received the bytes that've been sent by a server. The browser has converted the bytes to tags and has read through the tags to create a list of tokens.

This list of tokens then goes through the tree construction stage. The output of this stage is a **tree-like structure** - this is the DOM!

I want to point out two important quotes that Illya said in the video:

- >*a tree structure that captures the content and properties of the HTML and all the relationships between the nodes*

- >*the DOM is the full, parsed representation of the HTML*

**So the DOM is a model (representation) of the relationships and attributes of the HTML document that was received.** Remember that DOM stands for "Document Object Model". Something that I've found to be true as I've been learning is that to break something down, just read the thing backwards:

Document Object Model

...would become…

**Object Model of the Document!**

Remember that a JavaScript object is a tree-like structure that has properties and values. So the DOM can be accessed using a special object provided by the browser: `document`

Try this:

1. open the console on this page
2. type out the word `document`
    - careful not to declare it `const document`
    - careful not to wrap it in quotes `"document"`
3. press enter

The `document` object is provided by the browser and is a representation of the HTML document. This object is **not** provided by the JavaScript language. ECMAScript is the language specification that JavaScript is based on, and it only references the document object model in one place, in its "Global Object" section:

>*In addition to the properties defined in this specification the global object may have additional host defined properties. This may include a property whose value is the global object itself; for example, in the HTML document object model the window property of the global object is the global object itself. ([source](https://www.ecma-international.org/ecma-262/#sec-global-object))*

Basically, this says that the `document` object is not part of JavaScript, but is expected to **already** exist and be freely accessible to JavaScript code.

The DOM is standardized by the W3C. There are a number of specifications that make up the DOM, here are few:

- Core Specification
- Events Specification
- Style Specification
- Validation Specification
- Load and Save Specification

To see the full list of DOM specs, check out the [standard](https://www.w3.org/standards/techs/dom#w3c_all).

#### The DOM Recap

The DOM stands for "Document Object Model" and is a tree-like structure that is a representation of the HTML document, the relationship between elements, and contains the content and properties of the elements.

The DOM is **not**:

- part of the JavaScript language

The DOM is:

- constructed from the browser
- is globally accessible by JavaScript code using the `document` object

The DOM is used all of the time and is what we'll be using throughout this course!

#### Further Research

- [DOM Introduction](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
- [Section 8.2 Parsing HTML documents from the W3C's HTML Documentation](https://www.w3.org/TR/html5/syntax.html#parsing)
- [DOM Specification on W3C](https://www.w3.org/standards/techs/dom#w3c_all)
- [HTML Document Object Model mentioned in the ECMAScript Specification](https://www.ecma-international.org/ecma-262/#sec-global-object) - the language specification used by JavaScript

### Selecting Page Elements With CSS Selectors

Which of the following will style an element by its ID?

- [ ] `.left-nav { ... }`
- [ ] `.id { ... }`
- [x] `#footer { ... }`
- [ ] `p { ... }`

Which of the following will style the element by its class?

- [x] `.left-nav { ... }`
- [x] `.id { ... }`
- [ ] `#footer { ... }`
- [ ] `p { ... }`

Which of the following will style an element by targeting the tag name?

- [ ] `.left-nav { ... }`
- [ ] `.id { ... }`
- [ ] `#footer { ... }`
- [x] `p { ... }`

So this was a quick review on how to select elements by ID, class, and tag. Believe it or not, being able to select HTML elements this way is actually going to be a vital skill in this section where we learn how to access page elements using JavaScript and the DOM!

### Select Page Element By ID

`document.getElementById();`

For example: `document.getElementById('footer');`

One thing to notice right off the bat, is that we're passing `'footer'`, not `'#footer'`. It already knows that it's searching for an ID (its name is "getElementById", for a reason!).

If you'd like to read more about this method, check out its documentation page on MDN: https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById

Let's use this MDN documentation page to try out using this method.

[![MDN Documentation page](https://img.youtube.com/vi/HTwkHkERtvQ/0.jpg)](https://www.youtube.com/watch?v=HTwkHkERtvQ)

To recap what we just did:

- we opened the DevTools for the page we were looking at
- we switched to the Console pane
- we ran document.getElementById('content'); on the console

Running this code cause the `document` object to search through its entire tree-like structure for the element that has an ID of "content".

Now, what do you think will happen if you used `document.getElementById(<some-nonexistent-ID>)` to search for some ID that doesn't actually exist in the HTML page?

- [ ] a dummy element will be returned
- [ ] `false` will be returned
- [x] `null` will be returned
- [ ] it will cause an error

Which of the following will select the element with the ID of `logo`?

- [x] `document.getElementById('logo');`
- [ ] `document.getElementByID('logo');`
- [ ] `document.getElementByID('#logo');`
- [ ] `document.selectElementByID('logo');`

Write the DOM code to select the element with ID strawberry-banner.

`document.getElementById("strawberry-banner")`

#### Recap

In this section, we learned how to select a DOM element by its ID:

- `.getElementById()`

There are a couple of important things to keep in mind about this method:

- it is called on the document object
- it returns a **single** item

#### Further Research

[`.getElementById()` on MDN](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById) 

### Select Page Elements By Class Or Tag

#### Selecting Multiple Elements At Once

As I'm sure you remember from learning both HTML structure and CSS styling, an ID should be unique - meaning two or more elements should never have the same ID. Since IDs are unique, and since there will be only one element in the HTML with that ID, `document.getElementById()` will only ever return at most one element. So how would we select multiple DOM elements?

The next two DOM methods that we'll be looking at that both return multiple elements are:

- `.getElementsByClassName()`
- `.getElementsByTagName()`

Accessing Elements By Their Class: `document.getElementsByClassName('brand-color');`

Accessing Elements By Their Tag: `document.getElementsByTagName('p');`

Both `.getElementsByClassName()` and `.getElementsByTagName()` have an extra "s" in their name.

Write the DOM code to select all `<article>` elements:
`document.getElementsByTagName('article');`

Write the DOM code to select all elements with class: `fancy-footer`:
`document.getElementsByClassName('fancy-footer')`

We just saw that `.getElementsByClassName()` returns an array-like data structure of elements. But what exactly is an element?

#### Selecting Multiple Elements At Once Recap

In this section, we learned two ways to select multiple DOM elements:

- `.getElementsByClassName()`
- `.getElementsByTagName()`

There are a few important things to keep in mind about these two methods:

- both methods use the document object
- both return multiple items
- the list that's returned is not an array

#### Further Research

- [`.getElementsByClassName()` on MDN](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByClassName)
- [`.getElementsByTagName()` on MDN](https://developer.mozilla.org/en-US/docs/Web/API/Element/getElementsByTagName)

### Nodes, Elements, and Interfaces...Oh My

How the DOM is constructed in the correct order of operation:

- characters
- tags
- tokens
- nodes
- DOM

But what is a "node", exactly?

![node](https://d17h27t6h515a5.cloudfront.net/topher/2017/December/5a22d197_ud117-l1-interface-chain/ud117-l1-interface-chain.jpg)

>A "node", in this context, is simply an HTML element. The "DOM" is a tree structure that represents the HTML of the website, and every HTML element is a "node". See Document Object Model (DOM).
> 
> More specifically, "Node" is an interface that is implemented by multiple other objects, including "document" and "element". All objects implementing the "Node" interface can be treated similarly. The term "node" therefore (in the DOM context) means any object that implements the "Node" interface. Most commonly that is an element object representing a HTML element.
> https://stackoverflow.com/questions/24974621/what-is-a-node-in-javascript

### More Ways To Access Elements

#### The querySelector Method

We can use the `.querySelector()` method to select elements just like we do with CSS. We use the `.querySelector()` method and pass it a string that's just like a CSS selector:

```js
// find and return the element with an ID of "header"
document.querySelector('#header');

// find and return the first element with the class "header"
document.querySelector('.header');

// find and return the first <header> element
document.querySelector('header');
```

⚠️ `.querySelector()` Returns A Single Element ⚠️

This makes sense if you use it to search for an element by ID. However, even though `.getElementsByClassName()` and `.getElementsByTagName()` both return a list of multiple elements, using `.querySelector()` with a class selector or a tag selector will still only return the first item it finds.

#### The querySelectorAll Method

The `.querySelector()` method returns only one element from the DOM (if it exists). However, there are definitely times when you will want to get a list of all elements with a certain class or all of one type of element (e.g. all `<tr>` tags). We can use the `.querySelectorAll()` method to do this!

```js
// find and return a list of elements with the class "header"
document.querySelectorAll('.header');

// find and return a list of <header> elements
document.querySelectorAll('header');
```

#### Recap

In this section, we took a brief look the history of browser support for standard DOM methods, the rise of the jQuery library, and how jQuery's success brought about new DOM methods. The new DOM methods we looked at are

- `.querySelector()` - returns a single element
- `.querySelectorAll()` - returns a list of elements

```js
// find and return the element with an ID of "header"
document.querySelector('#header');

// find and return a list of elements with the class "header"
document.querySelectorAll('.header');
```

We also took a brief look that the list returned by `.querySelectorAll()` is a NodeList. We saw that it is possible to loop over a NodeList with either its `.forEach()` method, or the humble `for` loop:

```js
const allHeaders = document.querySelectorAll('header');

for(let i = 0; i < allHeaders.length; i++){
    console.dir(allHeaders[i]);
}
```

### Lesson summary

- DOM
- How DOM constructed
- Node and Element interfaces
- How to select elements
