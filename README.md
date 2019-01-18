# js_prac

(Learning JS Source) [https://developer.mozilla.org/en-US/docs/Learn/JavaScript]

## 1 What is JS?
The third layer of hte layer cake in standard web technologies over CSS and HTML

- HTML: Markup language to give structure and meaning to web content. Define paragraphs, heading and data tables and images.
```html
<p>Player 1: Chris</p>
```
- CSS: Style rules to apply styling to our HTML content
```css
p {
  font-family: 'helvetica neue', helvetica, sans-serif;
  letter-spacing: 1px;
  text-transform: uppercase;
  text-align: center;
  border: 2px solid rgba(0,0,200,0.6);
  background: rgba(0,0,200,0.3);
  color: rgba(0,0,200,0.6);
  box-shadow: 1px 1px 2px rgba(0,0,200,0.4);
  border-radius: 10px;
  padding: 3px 10px;
  display: inline-block;
  cursor: pointer;
}
```
- Javascript: Scripting language that enables dynamically updating content, control multimedia, animated images and such
```javascript
const para = document.querySelector('p');

para.addEventListener('click', updateName);

function updateName() {
  let name = prompt('Enter a new name');
  para.textContent = 'Player 1: ' + name;
}
```

#### Useful JS 
Consists alot of common programming features
- Storing variables
- Operations on pieces of texts (strings for example)
- Response to certain events on a web page. For exampel the click event that runs a code from above.

On top of this API (application programming interfaces) provide with extra stuff to do with javascript code. THese are ready made sets of code building blocks that allow a developer to implement programs that might be hard to do normally. 
**Browser API** are built into the web browser and expose data from surrounding computer environment or do complex things
- DOM API to manipulate HTML and CSS dynamically
- Geolocation API for geographical info
- Canvas and WebGL API for animated 2D and 3D graphics
- Audio and Video API to play audio and videos

**Third Party API** are not in the browser by default. We have to grab the code from somewhere on the map. Such as a twitter or google maps API

#### What is JS doing on your page
Recap of what happens when we load a web page
The code for HTML, CSS and JS are running inside the execution environment (browser).
HTML and CSS are assembled and made into a webpage. THEN the javascript engine is executed. SO basically HTML and CSS run first before javascript runs.

Javascript generally runs from top to bottom (the actual code). Basically like how any code works with functions and stuff. 

#### server side vs client side code
Client side = code on users computer. WHen a page is viewed the pages client side code is downloaded then run
In the following prac, server side is what we go through

Server side on the other hand runs on the server. 

#### javascript exampple
CSS uses link element to apply external syle sheets and uses style tag to apply internal stylesheets.
Javascript only uses the script element

[check code apply_javascript.html]


we can see that in the head tag we can put a script tag and put a specific script for the javascript.
However of course we can put the javascript in an external file

```css
<script src="script.js" async></script>
```
Then script.js will just have the javascript stuff

We can also apply javascript inside the HTML
```html
<button onclick="createParagraph()">Click me!</button>
```
In this example the the onclick handler is used to make the function run. However this is BAD PRACTICE and inefficient.

#### script loading strategies
Issues occur from getting scripts to load at the right time. Commonly HTML on a page is loaded in order of which it is appear. If we use javascript to manipulate elements on the page, the code won't work if the javascript is loaded and parsed before the HTML.
Above we see that the javascript is loaded in the head of the document, before the HTML is parsed which can cause an error

For an external script, we use **async** to make sure that the browser to continue the HTMl content once the script tag has been reached.
FOr an internal script we have to do 
```javascript
document.addEventListener("DOMContentLoaded", function() {
  ...
});
```
Which is used to signify that the HTML body is completely loaded and parsed.

#### async and defer
There are actually two ways with dealign the problem of a blocking script

async will download the script without blocking rendering the page and will execute as soon as the script finishes downloading. Best to use when the script in the page run indepdently from each other and doesn't depend on other scripts

defer will run the scripts in the order they appear in the page and execute them as soon as the script and content are downloaded
```html
<script defer src="js/vendor/jquery.js"></script>

<script defer src="js/script2.js"></script>

<script defer src="js/script3.js"></script>
```

#### adding variables
example
```javascript
let randomNumber = Math.floor(Math.random() * 100) + 1;
const guesses = document.querySelector('.guesses');
```
We can use let or var to set variables (differences explained later)
Const for values we don't want to chnage.

```html
const guesses = document.querySelector('.guesses');
```
Constants can be made to store a reference to the results in our paragraphs in our HTML, and are used to insert values into the paragraphs later on in the code. 

#### events
```javascript
guessSubmit.addEventListener('click', checkGuess);
```

We can create an action after a thing has been clicked (for example go to the checkGuess function)

#### loops
Same as any other programming language
```javascript
let resetParas = document.querySelectorAll('.resultParas p');
for (let i = 0 ; i < resetParas.length ; i++) {
  resetParas[i].textContent = '';
}
```

#### small brief on objects
In javascript everything is an object. The browser has alot of inbuilt objects but we can actually make our own ones.

```javascript
const guessField = document.querySelector('.guessField');
```
querySelector() method is from the document object. Which allows us to take on piece of information (a css selector) that selects the elements you want to reference to.

guessField contains a reference to input element it now has access to a number of properties in the object and also method (just like how java works. For example
```javascript
guessField.focus();
```
is a method that is used to ensure the cursor is focused in this location.

## 2 Debugging
Like any programming language errors can occur for different reasons

## 3 Programming basics in js
Most of this is just programming knowledge (sort of similar to java). Below are just some main points that I didn't know before already from the articles

#### variables
A variable is a container for a value. To declare a variable we do the following
```javascript
let myName;
let myAge;
```
It is dynamically typed like java, meaning we don't have to define a type for each variable.

Then we simply initialize it as normal
When we call let myName we are making an empty box. It's however not the same as not existing at all. Just a box with no value inside it yet.

```javascript
let myDog = 'Rover';
```
var and let are essentially the same, but let is used in modern versions of javascript which actually works somewhat differently (we don't have to know too much about it). But basically make sure that when we use let, declare the variable first then use it (if we use var it doesn't matter if we declare it first)

arrays are possible
```javascript
let myNameArray = ['Chris', 'Bob', 'Jim'];
```

#### numbers and operators
Everything in javascript uses the Number data type
```javascript
var myInt = 5;
var myFloat = 6.667;
myInt;
myFloat;
```
All the operators are basically the same as in any programming language

#### strings
```javascript
var string = 'The revolution will not be televised.';
string;
```
#### single quotes vs double quotes
```javascript
var sgl = 'Single quotes.';
var dbl = "Double quotes";
sgl;
dbl;
```
thankfully both of these have the same affect, so just choose one and be consistent

#### escaping characters in a string
Say we want to put a quote in our string. Then we have to escape it via \
```javascript
var bigmouth = 'I\'ve got no right to take my place...';
```
#### concat strings
```javascript
var button = document.querySelector('button');

button.onclick = function() {
  var name = prompt('What is your name?');
  alert('Hello ' + name + ', nice to see you!');
}
```
Simply using + to concat strings. If we end up concatenating a string and number it will still work as the number will just get converted to a string.

#### useful string methods
- Finding length of string: string.length
- Retrieving a specific string character: browserType\[browserType.length-1];
- Finding a substring inside a string
- Changing lower to upper case

#### arrays
Some useful methods for arrays
- length of array: array.length
- convert between string and array: string.split(',') --> split by comma
- add and remove elements: array.pop, array.push


## 3 Events
A simple example of how events work
```html
<button>Change color</button>
```

```javascript
var btn = document.querySelector('button');

function random(number) {
  return Math.floor(Math.random()*(number+1));
}

btn.onclick = function() {
  var rndCol = 'rgb(' + random(255) + ',' + random(255) + ',' + random(255) + ')';
  document.body.style.backgroundColor = rndCol;
}
```
A step by step analysis
1. Button is a html element
2. We store a reference to the button in a variable called btn using Document.querySelector()
3. Theres also a function which returns a random number
4. btn points to a button element, which can have a number of events happen on it (firing elements). 
5. So when the user actually clicks button. the button is clicked (method of btn) which then calles the function.

#### node.js
Different programming languages have their own set of event models and might work differently. A popular one is Node.js that enables devs to use js to build network and server side applications. The code can differ in these situations.

Another example is use javascript to build cross browser add ons using WebExtensions. The point of what this is saying is that events can differ in different programming environments

UP TO HERE: https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events

#### web events
```javascript
var btn = document.querySelector('button');

btn.onclick = function() {
  var rndCol = 'rgb(' + random(255) + ',' + random(255) + ',' + random(255) + ')';
  document.body.style.backgroundColor = rndCol;
}
```
The onclick property is the event handler property. When we set it to be equal to some code the code will run when the event fires on the button.

We can also set the handler property to be equal to a named function name.
```javascript
btn.onclick = bgChange;
```
There are many different event handler properties.
(EXAMPLE IN random-color.html)

#### inline event handlers (AVOID!!)
```html
<button onclick="bgChange()">Press me</button>
```
The attribute value is literally the javascript code we want to run. 
These are unmanageable and inefficient. You should never really mix up javascript and HTML as it becomes hard to parse. If we had 100 buttons it would be a nightmare

#### dom level 2 events



## 4 OBJECTS








