# js_prac

(Learning JS Source) [https://developer.mozilla.org/en-US/docs/Learn/JavaScript]

## 1 What is JS?
The third layer of hte layer cake in standard web technologies over CSS and HTML

- HTML: Markup language to give structure and meaning to web content. Define paragraphs, heading and data tables and images.
```html
<p>Player 1: Chris</p>
```
- CSS: Style rules to apply stylign to our HTML content
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


