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
  - [Introduction](#lesson1-introduction)
  - [The DOM](#the-dom)
  - [Selecting Page Elements With CSS Selectors](#selecting-page-elements-with-css-selectors)
  - [Select Page Element By ID](#select-page-element-by-id)
  - [Select Page Elements By Class Or Tag](#select-page-elements-by-class-or-tag)
  - [Nodes, Elements, and Interfaces...Oh My!](#nodes-elements-and-interfacesoh-my)
  - [More Ways To Access Elements](#more-ways-to-access-elements)
  - [Lesson summary](#lesson1-lesson-summary)
- [Lesson 2: Creating Content with JavaScript](#lesson-2-creating-content-with-javascript)
  - [Introduction](#lesson2-introduction)
  - [Update Existing Page Content](#update-existing-page-content)
  - [Add New Page Content](#add-new-page-content)
  - [Remove Page Content](#remove-page-content)
  - [Style Page Content](#style-page-content)
  - [Lesson summary](#lesson2-lesson-summary)
- [Lesson 3: Working with Browser Events](#lesson-3-working-with-browser-events)
  - [Introduction](#lesson3-introduction)

## Lesson 1: The Document Object Model

<a id="lesson1-introduction"></a>
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

#### Select Page Element By ID Recap

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

#### The `Node` Interface

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

#### Element Interface

Just like the Node Interface, the Element Interface is a blueprint for creating elements. One really important thing about the Element Interface is that it is a descendent of the Node Interface.

Since Element is pointing at Node, this indicates that the Element Interface inherits all of the Node Interface's properties and methods. This means that any element (lowercase "e"!) that was created from the Element Interface is also a descendent from the Node Interface...which means the element (lowercase "e"!) is also a node (lowercase "n"!).

#### Nodes, Elements, and Interfaces Recap

Hopefully this was an enlightening lesson on a number of fronts! You learned about interfaces, properties, and methods; an interface is like a blueprint, properties are like bits of information or data, and methods are functionality.

We also looked at a couple of specific interfaces:

- Node Interface
- Element Interface

We saw that both of these interfaces have properties and methods. We also saw how the Element Interface inherits all of the properties and methods from the Node interface.

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

#### More Ways To Access Elements Recap

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

<a id="lesson1-lesson-summary"></a>
### Lesson summary

- DOM
- How DOM constructed
- Node and Element interfaces
- How to select elements

## Lesson 2: Creating Content with JavaScript

<a id="lesson2-introduction"></a>
### Introduction 

#### Need to Know

To be successful in this section, there are a couple of things from the previous section that you need to know. You need to have a solid grasp of selecting DOM elements using:

- `document.getElementById()`
- `document.querySelector()`

Also, remember the Node Interface and the Element interface we went over in the previous section? Understanding how an interface determines the properties and methods for an element and understanding how to research an interface's properties and methods will be vital in this lesson.

If you get stuck, just jump back to the previous section that's giving you a bit of trouble.

#### Project Repository

Throughout this course, you'll learn skills and techniques to access and modify page content. There's no better way to demonstrate these skills than through trying them out on a real website! So I've created a copy of just the Udacity homepage. The project is on GitHub, so please clone the project to your local so that you can follow along.

Project repository: https://github.com/udacity/course-JS-and-the-DOM

### Update Existing Page Content

#### An Element's Inner HTML

Every element inherits properties and methods from the Element Interface (remember this from the previous lesson!). This means that every element has an `.innerHTML` **property**. This property, as it's rightly named, represents the markup of the element's content. We can use this property to:

- get an element's (and all of its descendants!) HTML content
- set an element's HTML content

What does `.innerHTML` return?

- [ ] a DOM element
- [ ] a Node
- [x] a string
- [ ] an array
- [ ] an object

If you look at this in the console, it looks like a string. Technically, however, what it returns is called a `DOMString`.

>💡 Innie vs Outie 💡
>The `.innerHTML` property sets or returns the HTML content inside the selected element (i.e. between the tags).
>
>There's also the rarely used `.outerHTML` property. `.outerHTML` represents the HTML element itself, as well as its children.

```js
<h1 id="pick-me">Greetings To <span>All</span>!</h1>

const innerResults = document.querySelector('#pick-me').innerHTML;
console.log(innerResults); // logs the string: "Greetings To <span>All</span>!"

const outerResults = document.querySelector('#pick-me').outerHTML;
console.log(outerResults); // logs the string: "<h1 id="pick-me">Greetings To <span>All</span>!</h1>"
```

#### An Element's Text Content

So `.innerHTML` will get/set an element's HTML content. If we just want the text content, we can use the fantastically named `.textContent` property!

The `.textContent` property will:

- set the text content of an element and all its descendants
- return the text content of an element and all its descendants

We just saw that passing text that contains HTML characters to `.textContent` will not display the content as HTML. Instead, it will still display everything as text - even the HTML characters!

If you'd like to update an element, including its HTML, then you need to use the `.innerHTML` property:

```js
myElement.textContent = 'The <strong>Greatest</strong> Ice Cream Flavors'; // doesn't work as expected

myElement.innerHTML = 'The <strong>Greatest</strong> Ice Cream Flavors';  // works as expected
```

#### An Element's Text Content - Version 2!

We can't close this section out without looking at the `.innerText` property!

Like the `.textContent` property, the `.innerText` property can be used to get/set an element's text content, but there are some important differences between the two properties.

`.textContent` sets/gets the text content of an element...pretty clear and simple.

`.innerText`, on the other hand, is a little tricker. Let's see this in action and then we'll discuss it!

As you saw, `.innerText` will get the visible text of the element. This is an important distinction! **If CSS is used to hide any text inside that element, `.innerText` will not return that text, while `.textContent` will return it.** And it's not just the hiding/showing nature of CSS that `.innerText` adheres to, `.innerText` will also honor changes to things like capitalization.

The `.textContent` property has been a standard for quite a long time. Conversely, `.innerText` property is a relatively new addition to the HTML specification. It has been around for a while but was not fully supported by all browser because it was not a part of the HTML specification.

Between `.textContent` and `.innerText`, you probably want to use `.textContent` since that will return all of the text no matter what. Rarely will you actually want only the visible text.

#### Update Existing Content Recap

In this section, we looked at multiple ways to change page content:

- `.innerHTML`
- `.textContent`
- `.innerText`

We saw that to set HTML content for an element, out of the three properties list above, we can only use `.innerHTML`. Using `.textContent` will erroneously include the HTML characters as plain text inside the element.

We also looked at the difference between `.textContent` and `.innerText`. **`.textContent` completely ignores any CSS styling** and returns all of the element's HTML just as it's listed in the HTML. On the other hand, the **`.innerText` property will take CSS styling into consideration** and will return the text that is visibly rendered on the page.


### Add New Page Content

You've learned about the document object, the Node Interface, and the Element interface. Where does `.createElement()` come from?

- [x] the `document` object
- [ ] the Node interface
- [ ] the element interface

Which of the following would create a new paragraph element?

- [x] `document.createElement('p')`
- [ ] `element.createElement('p')`
- [ ] `document.createElement('paragraph')`

#### Adding Content To The Page

You may have noticed that using `document.createElement()` to create an element didn't actually add that newly created element anywhere on the page! Creating an element...just creates it. **It doesn't add it to the DOM.** Since the element isn't added to the DOM, it doesn't appear in the page (if you remember, the DOM is the parsed representation of the page). So, now that we can create brand new elements, we need to be able to add them to the DOM so that they'll show up on the page.

We can use the `.appendChild()` method to add an element to the page! Before we see how this element works, let's quickly define the word "append". There are several different definitions of the word, but I like the wording of the Cambridge Dictionary's the best:

> to add something to the end of a piece of writing

Now, to use the `.appendChild()` method, it needs to be called on another element, not the document object!

```js
// create a brand new <span> element
const newSpan = document.createElement('span');

// select the first (main) heading of the page
const mainHeading = document.querySelector('h1');

// add the the <span> element as the last child element of the main heading
mainHeading.appendChild(newSpan);
```

>⚠️ `.appendChild()` Needs An Element! ⚠️  
>This is stated above, but I wanted to call this out, specifically. When you're using the `.appendChild()` method, it must be called on an existing element. To be clear, you can't call this on the `document` object, so the following will result in an error:

```js
const newSpan = document.createElement('span');

// causes an error
document.appendChild(newSpan);
```

#### Creating Text Nodes

Just like you created new elements with the `.createElement()` method, you can also create new text nodes using the `.createTextNode()` method. Take a look at the following code that:

- creates an paragraph element
- creates a text node
- appends the text node to the paragraph
- appends the paragraph to the tag

```js
const myPara = document.createElement('p');
const textOfParagraph = document.createTextNode('I am the text for the paragraph!');

myPara.appendChild(textOfParagraph);
document.body.appendChild(myPara);
```

However, since you already know about the `.textContent` property, the code below will provide the exact same result:

```js
const myPara = document.createElement('p');

myPara.textContent = 'I am the text for the paragraph!';
document.body.appendChild(myPara);
```

Therefore, instead of creating a new text node and appending it to an element, it's **faster and easier** to just update the element's text with the `.textContent` property.

What happens after running this code?

```js
const mainHeading = document.querySelector('#main-heading');
const otherHeading = document.querySelector('#other-heading');
const excitedText = document.createElement('span');

excitedText.textContent = '!!!';
mainHeading.appendChild(excitedText);
otherHeading.appendChild(excitedText);
```

- [ ] only mainHeading has three exclamation marks
- [x] only otherHeading has three exclamation marks
- [ ] both headings have three exclamation marks
- [ ] neither has any exclamation marks

> The `.appendChild()` method will move an element from its current position to the new position.

#### Inserting HTML In Other Locations

By definition, the `.appendChild()` method will add an element as the last child of the parent element. It's impossible to put it as the first child or anywhere else...it has to be the last child. Wouldn't it be nice if there were a little flexibility in where we could add the child element?

Enter the `.insertAdjacentHTML()` method! The `.insertAdjacentHTML()` method has to be called with two arguments:

- the location of the HTML
- the HTML text that is going to be inserted

The first argument to this method will let us insert the new HTML in one of four different locations

- `beforebegin` – inserts the HTML text as a previous sibling 
- `afterbegin` – inserts the HTML text as the first child 
- `beforeend` – inserts the HTML text as the last child 
- `afterend` – inserts the HTML text as a following sibling

A visual example works best, and MDN's documentation has a fantastic example that I'll modify slightly:

```html
<!-- beforebegin -->
<p>
    <!-- afterbegin -->
    Existing text/HTML content
    <!-- beforeend -->
</p>
<!-- afterend -->
```

Here's how we'd call `.insertAdjacentHTML()`:

```js
const mainHeading = document.querySelector('#main-heading');
const htmlTextToAdd = '<h2>Skydiving is fun!</h2>';

mainHeading.insertAdjacentHTML('afterend', htmlTextToAdd);
```

#### Add New Page Content Recap

In this section, we learned how to create new DOM elements and add them to the page. We looked at the following methods:

- `.createElement()` to create new elements
- `.appendChild()` to add a child element to a parent element as its last child
- `.createTextNode()` to create a text node
- `.insertAdjacentHTML()` to put HTML text anywhere around an element

Some important things to note are:

- if an element already exists in the DOM and this element is passed to `.appendChild()`, the `.appendChild()` method will move it rather than duplicating it
- an element's `.textContent` property is used more often than creating a text node with the `.createTextNode()` method
- the `.insertAdjacentHTML()` method's second argument has to be text, you can't pass an element. `.insertAdjacentElement()` will serve the purpose if you want to pass an element.

### Remove Page Content

#### What's in store!

In this quick section, you're going to learn how to remove content from the page. Specifically, we'll look at these new methods:

- `.removeChild()`
- `.remove()`

In the process, you'll also learn about these two properties:

- `.firstElementChild`
- `.parentElement`

#### Removing a Child Element

We can use the `.removeChild()` method to...wait for it...remove a child element. Basically, this is exactly the opposite of the `.appendChild()` method. So just like the `.appendChild()` method, the `.removeChild()` method requires:

- a parent element
- the child element that will be removed

```js
<parent-element>.removeChild(<child-to-remove>);
```

#### A drawback (and workaround!) with the `.removeChild()` Method

Just like the `.appendChild()` method, there's a (somewhat minor) drawback to the `.removeChild()` method. Both methods:

- require access to parent to function

However, we don't actually need to have the parent element because there is a workaround! Just like the `.firstElementChild` property can be called on a parent element to access its first element, every element also has a `parentElement` property that refers to its parent! So if we have access to the child element that we're about to add or remove, you can use the `parentElement` property to "move focus" to the element's parent. Then we can call `.removeChild()` (or `.appendChild()`) on that referenced parent element.

```js
const mainHeading = document.querySelector('h1');

mainHeading.parentElement.removeChild(mainHeading);
```

#### Removing a Child Element (Part 2!)

We went through all of those steps selecting an element, using DOM traversal techniques like `.parentElement` and `.firstElementChild`, so that we can remove a child element. I showed you this way so that you can get some exposure and practice to moving around in the DOM.

Now, you might be glad (or frustrated! haha) to find out there's an easier way to do all this! We can move the child element directly with the `.remove()` method:

```js
const mainHeading = document.querySelector('h1');

mainHeading.remove();
```

#### Remove Page Content Recap

In this short section, we learned two ways to remove an element from the page. You learned about:

- `.removeChild()`
- `.remove()`

The difference is that with `.removeChild()` must be called on the parent of the element being removed and must be passed the child to be removed, while `.remove()` can be called directly on the element to delete.

We also learned about the following helpful properties:

- `.firstChild`
- `.firstElementChild`
- `.parentElement`

The difference between `.firstChild` and `.firstElementChild`, is that `.firstElementChild` will always return the first element, while `.firstChild` might **return whitespace** (if there is any) to preserve the formatting of the underlying HTML source code.

### Style Page Content

In this section, we'll be looking at controlling page and element styling using the following properties and methods:

- `.style.<prop>`
- `.cssText()`
- `.setAttribute()`
- `.className`
- `.classList`

Before we begin, put these in the correct order of CSS specificity. Put the least-specific option at the top and the most-specific option at the bottom.

<table>
    <tr>
        <th>LEVEL OF SPECIFICITY</th>
        <th>CSS RULE</th>
    </tr>
    <tr>
        <td>Least specific</td>
        <td>rules in a stylesheet</td>
    </tr>
        <td>More specific</td>
        <td>rules in a &ltstyle&gt tag</td>
    <tr>
        <td>Most specific</td>
        <td>rules in a tag's style attribute</td>
    </tr>
</table>

> Basically, the closer the style rule is to an element, the more specific it is. For example, a rule in a style attribute on an element will override a style rule for that element in a CSS stylesheet. There is also the specificity of the type of selector being used. An _ID_ is more specific than a class.

#### Modifying an Element's Style Attribute

Let's jump back to your knowledge of CSS. When trying to style an element, the most-specific rules that you can write for an element are written in that element's `style` attribute. Lucky for us, we can access access an element's `style` attribute using the `.style` property!

```js
const mainHeading = document.querySelector('h1');

mainHeading.style.color = 'red';
```

Now, I want to point out that when using the `.style` property, you can only modify one CSS style at a time. That's why the previous code has `.style.color = 'red'` and not just `.style = 'red'`.

#### Adding Multiple Styles At Once

We've seen how the `.style.<property>` syntax will let us change just one piece of styling for an element. So if we wanted to set an element's color, background color, and font size, we'd have to use three separate lines of code:

```js
const mainHeading = document.querySelector('h1');

mainHeading.style.color = 'blue';
mainHeading.style.backgroundColor = 'orange';
mainHeading.style.fontSize = '3.5em';
```

...and that's just for setting three styles. Imagine if we needed 15 or 20 different styles! So the `.style.property` syntax is perfect for setting one style at a time, but it's not great for controlling multiple styles.

Fortunately, we can use the `.style.cssText` property to set multiple CSS styles at once!

```js
const mainHeading = document.querySelector('h1');

mainHeading.style.cssText = 'color: blue; background-color: orange; font-size: 3.5em';
```

Notice that when using the `.style.cssText` property, you write the CSS styles just as you would in a stylesheet; so you write `font-size` rather than `fontSize`. This is different than using the individual `.style.<property>` way.

#### Setting An Element's Attributes

Another way to set styles for an element is to bypass the `.style.<property>` and `.style.cssText` properties altogether and use the `.setAttribute()` method:

```js
const mainHeading = document.querySelector('h1');

mainHeading.setAttribute('style', 'color: blue; background-color: orange; font-size: 3.5em;');
```

The `setAttribute()` method is not just for styling page elements. You can use this method to set any attribute for an element. If you want to give an element an ID, you can do that!:

```js
const mainHeading = document.querySelector('h1');

// add an ID to the heading's sibling element
mainHeading.nextElementSibling.setAttribute('id', 'heading-sibling');

// use the newly added ID to access that element
document.querySelector('#heading-sibling').style.backgroundColor = 'red';
```

#### Accessing an Element's Classes

The first element property we'll look at is the `.className` property. This property returns a string of all of the element's classes. If an element has the following HTML:

```html
<h1 id="main-heading" class="ank-student jpk-modal">Learn Web Development at Udacity</h1>
```

We could use .className to access the list of classes:

```js
const mainHeading = document.querySelector('#main-heading');

// store the list of classes in a variable
const listOfClasses = mainHeading.className;

// logs out the string "ank-student jpk-modal"
console.log(listOfClasses);
```

The `.className` property returns a space-separated string of the classes. This isn't the most ideal format, unfortunately. We can, however, convert this space-separated string into an array using the JavaScript string method, `.split()`:

```js
const arrayOfClasses = listOfClasses.split(' ');

// logs out the array of strings ["ank-student", "jpk-modal"]
console.log(arrayOfClasses);
```

Now that we have an array of classes, we can do any data-intensive calculations:

- use a for loop to loop through the list of class names
- use `.push()` to add an item to the list
- use `.pop()` to remove an item from the list

`.className` is a property, so we can set its value just by assigning a string to the property:

```js
mainHeading.className = "im-the-new-class";
```

The above code erases any classes that were originally in the element's `class` attribute and replaces it with the single class `im-the-new-class`.

Since `.className` returns a string, it makes it hard to add or remove individual classes. As I mentioned earlier, we can convert the string to an array and then use different Array Methods to search for a class remove it from the list, and then update the `.className` with the remaining classes. However, we don't want to do all of that work! Let's use the newer `.classList` property.

#### The `.classList` Property

The `.classList` property is newer than the `.className` property, but is much nicer, check it out:

```html
<h1 id="main-heading" class="ank-student jpk-modal">Learn Web Development at Udacity</h1>
```

```js
const mainHeading = document.querySelector('#main-heading');

// store the list of classes in a variable
const listOfClasses = mainHeading.classList;

// logs out ["ank-student", "jpk-modal"]
console.log(listOfClasses);
```

The `.classList` property has a number of properties of its own. Some of the most popularly used ones are:

- `.add()` - to add a class to the list
- `.remove()` - to remove a class from the list
- `.toggle()` - to add the class if it doesn't exists or remove it from the list if it does already exist
- `.contains()` - returns returns a boolean based on if the class exists in the list or not

#### Style Page Content Recap

We learned a ton of content in this section! We looked at:

- modifying individual styles with `.style.<prop>`
- updating multiple styles at once with `.style.cssText`
- getting/setting a list of classes with `.className`
- getting/setting/toggling CSS classes with `.classList`

My recommendation to you is that, out of the list of techniques you learned in this section, to use the `.classList` property more than any other. `.classList` is by far the **most helpful** property of the bunch, and it helps to keep your CSS styling out of your JavaScript code.

<a id="lesson2-lesson-summary"></a>
### Lesson summary

- Update page content
- Add new content
- Remove content
- Style content

## Lesson 3: Working with Browser Events

<a id="lesson3-introduction"></a>
### Introduction

#### Lesson Overview
To recap, we'll be looking at :

- Events - what they are
- Responding to an event - how to listen for an event and respond when one happens
- Event Data - harness the data that is included with an event
- Stopping an event - preventing an event from triggering multiple responses
- Event Lifecycle - the lifecycle stages of an event
- DOM Readiness - events to know when the DOM itself is ready to be interacted with

#### Seeing An Event
There is a hidden world of events going on right now on this very page! It's really hard to actually see into this hidden world, though. So how can we know that events really are being announced? If they are being announced, how come they're not easy for us to see?

Fortunately, the Chrome browser has a special `monitorEvents()` function that will let us see different events as they are occurring.

The monitorEvents function will keep spitting out all of the events that are happening on the targeted element until the end of time...that, or until you refresh the page. Alternatively, the Chrome browser does offer an `unmonitorEvents()` function that will turn off the announcing of events for the targeted element:

```javascript
// start displaying all events on the document object
monitorEvents(document);

// turn off the displaying of all events on the document object.
unmonitorEvents(document);
```

One last little bit of info on `monitorEvents` is that this is for development/testing purposes only. It's not supposed to be used for production code.
