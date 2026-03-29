# el.js

[![Ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/gugusdarmayanto)

A lightweight, chainable DOM manipulation library for modern JavaScript applications.

## Installation

### CDN (Recommended for Quick Start)

#### jsDelivr
```html
<script src="https://cdn.jsdelivr.net/npm/@slice-code/el.js@1.0.4/el.js"></script>
```

#### unpkg
```html
<script src="https://unpkg.com/@slice-code/el.js@1.0.4/el.js"></script>
```

#### ESM via CDN
```javascript
import el from 'https://cdn.jsdelivr.net/npm/@slice-code/el.js@1.0.4/el.js';
```

### NPM
```bash
npm install @slice-code/el.js
```

### ES Module
```javascript
import el from './el.js';
```

### Script Tag (Local)
```html
<script src="./el.js"></script>
<script>
  // el is available globally
  const div = el('div').text('Hello World').get();
</script>
```

## Quick Start

```javascript
import el from './el.js';

// Create a simple element
const app = el('div')
  .id('app')
  .class('container')
  .text('Hello World')
  .get();

document.body.appendChild(app);

// Create nested elements
const card = el('div')
  .class('card')
  .child([
    el('h2').text('Card Title'),
    el('p').text('Card description here'),
    el('button').text('Click Me').click(() => alert('Clicked!'))
  ])
  .get();
```

## Features

### 1. Element Creation

```javascript
// Create any HTML element
el('div')      // creates <div>
el('span')     // creates <span>
el('button')   // creates <button>
el('input')    // creates <input>
el('form')     // creates <form>

// Create SVG elements (automatically handled)
el('svg')      // creates <svg>
el('circle')   // creates <circle>
el('rect')     // creates <rect>
el('path')     // creates <path>

// Create from existing DOM element
const existingDiv = document.getElementById('myDiv');
el(existingDiv).text('Updated text');
```

### 2. Attributes

| Method | Description | Example |
|--------|-------------|---------|
| `id(name)` | Sets element ID | `el('div').id('myId')` |
| `class(name, replace)` | Adds CSS classes | `el('div').class('btn primary')` |
| `attr(name, value)` | Sets any attribute | `el('input').attr('type', 'email')` |
| `data(key, value)` | Sets data attribute | `el('div').data('id', '123')` |
| `aria(key, value)` | Sets ARIA attribute | `el('div').aria('label', 'Menu')` |
| `name(value)` | Sets name attribute | `el('input').name('username')` |
| `type(value)` | Sets type attribute | `el('input').type('text')` |
| `href(url)` | Sets href attribute | `el('a').href('https://example.com')` |
| `src(url)` | Sets src attribute | `el('img').src('image.png')` |
| `value(val)` | Sets input value | `el('input').value('default')` |
| `required()` | Sets required attribute | `el('input').required()` |
| `disabled(bool)` | Toggles disabled state | `el('input').disabled(true)` |
| `checked(bool)` | Sets checked state | `el('input').checked(true)` |
| `placeholder(text)` | Sets placeholder | `el('input').placeholder('Enter name')` |

### 3. Content

| Method | Description | Example |
|--------|-------------|---------|
| `text(content)` | Sets text content | `el('p').text('Hello')` |
| `html(html)` | Sets inner HTML | `el('div').html('<b>Bold</b>')` |
| `textContent(content)` | Sets textContent | `el('div').textContent('Text')` |
| `clear(resetScroll)` | Clears innerHTML | `el('div').clear()` |
| `empty()` | Clears content and children | `el('div').empty()` |

### 4. Styling

#### Individual Style Methods

```javascript
el('div')
  .width('100px')
  .height('50px')
  .padding('10px')
  .margin('20px')
  .background('#3b82f6')
  .color('#ffffff')
  .border('1px solid #000')
  .radius('8px')
  .boxShadow('0 4px 6px rgba(0,0,0,0.1)')
  .opacity('0.9')
  .zIndex('100');
```

#### CSS Object Method

```javascript
el('div').css({
  'background-color': '#3b82f6',
  'color': 'white',
  'padding': '20px',
  'border-radius': '8px'
});
```

#### Layout Methods

```javascript
// Flexbox
el('div')
  .flex('row')        // display: flex, flexDirection: row
  .justify('center')  // justifyContent: center
  .items('center')    // alignItems: center
  .gap('10px')        // gap: 10px
  .wrap('wrap');      // flexWrap: wrap

// Grid
el('div')
  .grid('repeat(3, 1fr)')  // display: grid, gridTemplateColumns
  .gap('20px');

// Position
el('div')
  .fixed()        // position: fixed
  .top('0')
  .left('0')
  .right('0');

// Visibility
el('div').hide();     // display: none
el('div').show();     // display: ''
el('div').toggle();   // toggle display
```

#### All Style Methods

| Method | Method | Method | Method |
|--------|--------|--------|--------|
| `width()` | `height()` | `minWidth()` | `minHeight()` |
| `maxWidth()` | `maxHeight()` | `padding()` | `margin()` |
| `marginTop()` | `marginBottom()` | `marginLeft()` | `marginRight()` |
| `border()` | `borderTop()` | `borderBottom()` | `borderLeft()` |
| `borderRight()` | `radius()` | `outline()` | `background()` |
| `backgroundImage()` | `backgroundSize()` | `backgroundRepeat()` | `backgroundPosition()` |
| `color()` | `font()` | `size()` | `fontWeight()` |
| `lineHeight()` | `align()` | `display()` | `opacity()` |
| `zIndex()` | `overflow()` | `overflowX()` | `overflowY()` |
| `boxShadow()` | `transform()` | `transition()` | `cursor()` |
| `float()` | `top()` | `bottom()` | `left()` |
| `right()` | `fixed()` | | |

### 5. Class Manipulation

```javascript
// Add class
el('div').class('btn primary');

// Replace all classes
el('div').class('new-class', true);

// Remove class
el('div').removeClass('btn');

// Toggle class
el('div').toggleClass('active');

// Check if has class
if (el('div').hasClass('active')) {
  // ...
}

// Clear all classes
el('div').clearClass();
```

### 6. Event Handling

```javascript
// Click
el('button').click(() => console.log('Clicked!'));

// Double click
el('div').dblclick(() => console.log('Double clicked!'));

// Hover
el('div').hover(
  () => console.log('Enter'),   // mouseenter
  () => console.log('Leave')    // mouseleave
);

// Input events
el('input')
  .input((e) => console.log('Input:', e.target.value))
  .change((e) => console.log('Changed:', e.target.value))
  .keyup((e) => console.log('Key:', e.key))
  .keydown((e) => console.log('Key:', e.key))
  .keypress((e) => console.log('Key pressed'));

// Focus & Blur
el('input')
  .focus(() => console.log('Focused'))
  .blur(() => console.log('Blurred'));

// Mouse events
el('div')
  .mouseover(() => console.log('Mouse over'))
  .mouseout(() => console.log('Mouse out'))
  .mousedown(() => console.log('Mouse down'))
  .mouseup(() => console.log('Mouse up'));

// Touch events
el('div')
  .touchstart(() => console.log('Touch start'))
  .touchend(() => console.log('Touch end'))
  .touchmove(() => console.log('Touch move'));

// Scroll & Wheel
el('div')
  .scroll(() => console.log('Scrolling'))
  .wheel(() => console.log('Wheel'));

// Context menu (right-click)
el('div').contextmenu((e) => {
  e.preventDefault();
  console.log('Custom context menu');
});

// Custom event
el('div').on('customEvent', (e) => console.log('Custom event'));

// Remove event listener
const handler = () => console.log('Click');
el('button').click(handler);
// Later...
el('button').off('click', handler);
```

### 7. Form Handling

```javascript
// Form submission (returns parsed JSON)
el('form').submit((data) => {
  console.log('Form data:', data);
  // data = { username: 'value', email: 'value', ... }
});

// Get/Set values
el('input').value('New value');
const val = el('input').getValue(); // or getVal()

// Checkbox/Radio
el('input').type('checkbox').checked(true);
```

### 8. DOM Traversal

```javascript
// Find elements
const child = el('div').find('.child');      // single element
const children = el('div').findAll('.item'); // array of elements

// Get parent
const parent = el('div').getParent();

// Get children
const children = el('div').getChildren();

// Get siblings
const siblings = el('div').getSiblings();

// Get index
const index = el('div').getIndex();

// Navigate
const next = el('div').next();     // next sibling
const prev = el('div').prev();     // previous sibling
const first = el('div').first();   // first child
const last = el('div').last();     // last child
const item = el('div').eq(2);      // child at index 2

// Closest ancestor
const ancestor = el('span').closest('.container');
```

### 9. Child Elements

```javascript
// Add child
el('div').child(el('p').text('Child'));

// Add multiple children
el('div').child([
  el('h1').text('Title'),
  el('p').text('Paragraph'),
  el('button').text('Button')
]);

// Add array of children
const items = ['Item 1', 'Item 2', 'Item 3'].map(item => 
  el('li').text(item)
);
el('ul').child(items);

// Add Promise child (shows placeholder until resolved)
el('div').child(
  fetch('/api/data').then(r => el('div').text('Loaded!'))
);

// Prepend child
el('div').prepend(el('p').text('First'));

// Replace content
el('div').replace(el('p').text('New content'));

// Get the DOM element
const domElement = el('div').get();
```

### 10. Utility Methods

```javascript
// Getters
const html = el('div').getHtml();
const text = el('div').getText();
const val = el('input').getVal();
const attr = el('div').getAttr('data-id');
const data = el('div').getData('id');
const style = el('div').getStyle('background-color');
const width = el('div').getWidth();
const height = el('div').getHeight();

// Focus/Blur
el('input').focus();  // focus element
el('input').blur();   // blur element

// Select all text
el('input').selectAll();

// Scroll
el('div').scrollTo(0, 100);
el('div').scrollIntoView();

// Remove element
el('div').remove();

// Remove attribute
el('div').attrRemove('disabled');

// Remove style property
el('div').styleRemove('background-color');

// Set tabIndex
el('div').index(0);

// Set draggable
el('div').draggable().dragStart((e) => {
  e.dataTransfer.setData('text/plain', 'dragging');
});

// Content editable
el('div').design(true);  // enable editing
```

### 11. Special Features

#### loopFunc (Auto-stopping Loop)

Automatically stops when element is removed from DOM:

```javascript
el('div').loopFunc((element) => {
  element.textContent = new Date().toLocaleTimeString();
}, 1000); // Update every second

// Loop automatically stops when element is removed
el('div').remove();
```

#### addModule

Add custom methods to elements:

```javascript
el('div').addModule('highlight', function() {
  this.style.background = 'yellow';
  return this;
});

el('div').el.highlight(); // Call custom method
```

#### link

Link element to an object for easy reference:

```javascript
const refs = {};
el('div').id('main').link(refs, 'mainDiv');

// Later access via
refs.mainDiv; // Returns the DOM element
```

#### load

Execute callback when element is ready:

```javascript
el('div').load((elm) => {
  console.log('Width:', elm.width);
  console.log('Height:', elm.height);
});
```

#### resize

Handle window resize:

```javascript
el('div').resize((elm) => {
  console.log('Window resized:', elm.width, 'x', elm.height);
});
```

## Complete Example

```javascript
import el from './el.js';

// Build a complete UI
const app = el('div')
  .class('app-container')
  .child([
    // Header
    el('header').class('header').child([
      el('h1').text('My App'),
      el('nav').child([
        el('a').href('#').text('Home').class('nav-link'),
        el('a').href('#').text('About').class('nav-link')
      ])
    ]),
    
    // Main content
    el('main').class('main-content').child([
      // Form
      el('form').id('contact-form').class('form').child([
        el('input')
          .type('text')
          .name('name')
          .placeholder('Your Name')
          .class('input')
          .required(),
        el('input')
          .type('email')
          .name('email')
          .placeholder('Your Email')
          .class('input')
          .required(),
        el('button')
          .type('submit')
          .text('Submit')
          .class('btn btn-primary')
      ]).submit((data) => {
        console.log('Form submitted:', data);
        // { name: '...', email: '...' }
      })
    ]),
    
    // Footer with counter
    el('footer').class('footer').child([
      el('p').text('Counter: 0').id('counter')
    ])
  ])
  .get();

document.body.appendChild(app);

// Start auto-updating counter
el(document.getElementById('counter')).loopFunc((el) => {
  const current = parseInt(el.textContent.replace('Counter: ', ''));
  el.textContent = 'Counter: ' + (current + 1);
}, 1000);
```

## API Reference Summary

| Category | Methods |
|----------|---------|
| **Creation** | `el(tag)`, `get()` |
| **Attributes** | `id()`, `class()`, `attr()`, `data()`, `aria()`, `name()`, `type()`, `href()`, `src()`, `value()`, `placeholder()`, `required()`, `disabled()`, `checked()` |
| **Content** | `text()`, `html()`, `textContent()`, `clear()`, `empty()` |
| **Styling** | `css()`, `width()`, `height()`, `padding()`, `margin()`, `border()`, `radius()`, `background()`, `color()`, `opacity()`, `boxShadow()`, `transform()`, `transition()`, + more |
| **Layout** | `flex()`, `grid()`, `justify()`, `items()`, `gap()`, `wrap()`, `show()`, `hide()`, `toggle()` |
| **Classes** | `class()`, `removeClass()`, `toggleClass()`, `hasClass()`, `clearClass()` |
| **Events** | `click()`, `dblclick()`, `hover()`, `input()`, `change()`, `keyup()`, `keydown()`, `focus()`, `blur()`, `submit()`, `scroll()`, `on()`, `off()`, + more |
| **Traversal** | `find()`, `findAll()`, `closest()`, `next()`, `prev()`, `first()`, `last()`, `eq()`, `getParent()`, `getChildren()`, `getSiblings()` |
| **Children** | `child()`, `prepend()`, `replace()`, `remove()` |
| **Getters** | `getValue()`, `getText()`, `getHtml()`, `getAttr()`, `getData()`, `getStyle()`, `getWidth()`, `getHeight()` |
| **Special** | `loopFunc()`, `load()`, `resize()`, `draggable()`, `design()`, `link()`, `addModule()` |

## Browser Support

el.js works in all modern browsers that support ES6+.

## License

MIT License

## Author

slice-code.click