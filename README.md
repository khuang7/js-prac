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





