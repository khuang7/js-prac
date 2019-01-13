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



