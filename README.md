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
A new type of event mechanism we have is the level 2 events specification. Which provides browsers with a new function
- addEventListener()
It works similarly to event handler but the syntax is different

```javascript
var btn = document.querySelector('button');

function bgChange() {
  var rndCol = 'rgb(' + random(255) + ',' + random(255) + ',' + random(255) + ')';
  document.body.style.backgroundColor = rndCol;
}   

btn.addEventListener('click', bgChange);
```
Inside addEvenListener there are two parameters. THe name of the event to register the handler, and the function it goes to.

There is also a removeEventListener which can remove a previous added listener.
```javascript
btn.removeEventListener('click', bgChange);
```

This remove function is useful for complex programs to clean up old unused handlers.
We can just register multiple handlers for the same listeners
```javascript
myElement.onclick = functionA;
myElement.onclick = functionB;
```
```javascript
myElement.addEventListener('click', functionA);
myElement.addEventListener('click', functionB);
```

#### which event mechanism to use?
Obviously HTML inline handlers are the worse and should never be used as mentioned above.

The other two are interchangeable.
Event handler properties have less power and options but are better for cross browser compatibality
DOM level 2 events are powerful but can be more complex and less supported.

#### Other Event Concepts
- Event Objects
- Preventing Default Behaviour
- Event Bubbling and Capture


## 4 OBJECTS
An object is a collection of related data, which usually have variables and functions. (Just like Java)
Creating an object begins with defining and initializing a variable. Alot of this chapter kind of reviews stuff about objects that are similar to Java. So I will have minimal notes on some of the concepts I don't already know.

#### Basics

The syntax for making objects is like this
```javascript
var objectName = {
  member1Name: member1Value,
  member2Name: member2Value,
  member3Name: member3Value
};
```
To access objects properties we use the dot notation
```javascript
person.age
person.interests[1]
person.bio()
```

#### Sub-namespaces
We can make the value of an object member antoher object
```javascript
name : {
  first: 'Bob',
  last: 'Smith'
},
```

Then we access it via
```javascript
person.name.first
person.name.last
```

#### bracket notation
Another way to access object properties
```javascript
person['age']
person['name']['first']
```
It looks like an array, but instead of numbers we use the name associated with each member's value.

#### Setting object members
Before we looked at getters now we look at setters
There are several ways
```javascript
person.age = 45;
person['name']['last'] = 'Cratchit';
person['eyes'] = 'hazel';
person.farewell = function() { alert("Bye everybody!"); }
```

#### this
The this keyword refers to the current object. 
```javacscript
greeting: function() {
  alert('Hi! I\'m ' + this.name.first + '.');
}
```
In this case arguably, you could use person instead of this. But this ensure it works for this context. Because it's possible that two different person objects instances may have different names.
Lets looks at this from an example point of view
```javascript
var person1 = {
  name: 'Chris',
  greeting: function() {
    alert('Hi! I\'m ' + this.name + '.');
  }
}

var person2 = {
  name: 'Brian',
  greeting: function() {
    alert('Hi! I\'m ' + this.name + '.');
  }
}
```
In this case if we do person1.greeting() and person2.greeting() it will give a different outpu but both refer to the same method.

#### Constructor
To create an instance of a class. A constructor is needed. Constructors provide the means to create as many objects as we need in an effective way.v . (more in oojs.html code)

#### Alternate way to create objects
We cano use the object() constructor to create a new object and add stuff on it after
```javascript
var person1 = new Object();
```
Then we can add properties and methods on the go
```javascript
person1.name = 'Chris';
person1['age'] = 38;
person1.greeting = function() {
  alert('Hi! I\'m ' + this.name + '.');
};
```

#### Another alternate way to create objects
Javascript has a built in method called create(). Which is useful if we are only creating a few instances of an object.
```javascript
var person2 = Object.create(person1);
```
We can see that we created an object based on person1. 

What create actually does is create a new object from a specified prototype object (explained below)
```javascript
person2.__proto__
```
which returns person1


#### prototype based language
To provide inheritance, objects can have a prototype object. Which is like a template object that it inherits methods and properties from. The properties and methods defined on the prototype property on the Objects constructor functions, not the object instance themselves.

An example
```javascript
function Person(first, last, age, gender, interests) {
  
  // property and method definitions
  this.first = first;
  this.last = last;
//...
}

var person1 = new Person('Bob', 'Smith', 32, 'male', ['music', 'skiing']);
```

If we type person1. there is a bunch of autocomplete options in the java console. In this list person() will pop up (the constructor) and also other stuff like name, age and some other weird ones like watch, valueOf which are actually defined in the Person() prototype object which is Object.

person1 inherits from prototype person which inherits from prototype Object.
If we do
```javascript
person1.valueOf()
```
Browser will check to see if Person object has valueOf() method. It doesn't clearly. So therefore it checks to see if Person() constructor's prototype object has a value Of. It does so then it is called.

#### object
If we check out the objects page we see that on the list there a a numebr of properties and methods. Some are inherited but some are not.
The inherited ones are the ones defined in the PROTOTYPE property. So ones that begin in Object.prototype and not Object.
The prototypes property value is an object, which is a bucket for storing properties and methods that can be inherited by objects down the line.

In a nutshell. Object.prototype.ANYTHING can be inherited
Object.ANYTHING cannot be inherited and only used by object itself


#### constructor property
Every constructor function has a prototype porerty whose value is an object containing a constructor property. 
```javascript
person1.constructor
person2.constructor
```
Both of these will return the Person() constructor (the original definition of these instances)
The constructor is a function, so it can be invoked using parantheses. 

A clever trick is to put parentheses at the end of the constructor property to create another object instances from that constructor. 
```javascript
var person3 = new person1.constructor('Karen', 'Stephenson', 26, 'female', ['playing drums', 'mountain climbing']);
```
This is ueful if we want to create a new instance and not have an eas reference to the original constructor

#### modifying prototypes
```javascript
Person.prototype.farewell = function() {
  alert(this.name.first + ' has left the building. Bye for now!');
};
```
This adds a new method to the constructor's prototype property

If we run person1.farewell(). This will create the alert with the person's name correctly. This is USEFUL
THe whole inheritance chain is updated dynamiocally and automatticaly, making this new method available on all object instances dervied from the constructor

In the code we define the constructor. Create an instance object from the construtor. Then add a new method to the constructor's prototype. The farewell() method is still available on the person1 object instance. Its members have been automatically update to include the new farewell function.

Its rare to see properties defined on the prototype property. Because it is not flexible. 
It is a common pattern to define the properties inside the constructor and the methods on the prototype

```javascript
// Constructor with property definitions

function Test(a, b, c, d) {
  // property definitions
}

// First method definition

Test.prototype.x = function() { ... };

// Second method definition

Test.prototype.y = function() { ... };

// etc.
```


#### Inheritance
#### JSON data


## 5 Client Side Web API







