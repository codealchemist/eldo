# el.js

Tiny chainable DOM manipulation lib.

## Install

`npm i el.js`

Or just download `index.js`.

## Usage

Add **El.js** to your project:

`<script src="path/el.js"></script>`

Create an instance for the element you want to manipulate, for example,
let's grab a button with the id `coolButton`, which is rendered in hidden
state with the style `display: none`, make it visible and disable it when clicked:

```
const $coolButton = new El('#coolButton')
$coolButton
  .show()
  .on('click', () => $coolButton.disable())
```

## Chaining

Once you created an instance you can chain API methods if you need to do multiple
manipulations of your element.

For example:

```
const $title = new El('#title')
$title
  .html('Alice in Chains rocks!')
  .addClass('cool')
  .show()
```

## API

- `constructor(element)`
- `exists()`
- `get()`
- `show()`
- `showInline()`
- `hide()`
- `disable()`
- `enable()`
- `style(styleName, value)`
- `addClass(className)`
- `removeClass(className)`
- `remove()`
- `setRandomBackground({path = '', range = [0, 5], length = 3, ext = 'jpg'})`
- `appear()`
- `disappear()`
- `focus()`
- `html(value)`
- `appendHtml(value)`
- `prependHtml(value)`
- `val(value)`
- `clear()`
- `isVisible()`
- `toggle()`
- `caretEnd()`
- `src(value)`
- `scrollBottom()`
- `on(event, callback)`
- `static injectStyles(styles)`


### Create new instance

`constructor (element)`

Where `element` can be any valid CSS selector or a reference to an element.

For the HTML:
```
<ul class="user-list">
 ...
</ul>
```
It's valid to construct an instance with:
`const $userList = new El('.user-list')`

And:
```
const userListElement = document.querySelector('.user-list')
const $userList = new El(userListElement)
```

### Does the element exists?

`$myEl.exists()`

Returns a boolean.

### Get a reference to the element
`$myEl.get()`

### Show a hidden element
`$myEl.show()`

Works with elements hidden with `display: none` by switching to `display: block`.

### Show a hidden element inline
`$myEl.showInline()`

Works with elements hidden with `display: none` by switching to `display: inline`.

### Hide element
`$myEl.hide`

Hides an element using `display: none`.

### Disable element

`$myEl.disable()`

Sets `disabled` attribute to `true`.

### Enable element

`$myEl.disable()`

Sets `disabled` attribute to `false`.

### Get all styles on element

`$myEl.style()`

Returns styles object containing all styles set on element.

### Get specific style on element

`$myEl.style('color')`

Returns requested style value.

### Set style on element

`$myEl.style('color', 'black')`

Sets passed style attribute with passed value.

### Get attribute

`$myEl.attr('data-id')`

Returns value for attribute `data-id`.

### Set attribute

`$myEl.attr('data-id', 42)`

Sets attribute `data-id` to `42`.

### Remove attribute

`$myEl.attr('data-id', false)`

Removes attribute `data-id` from element.

### Add class to element

`$myEl.addClass('active')`

Appends passed class to element's `className` attribute.

### Remove class from element

`$myEl.removeClass('active')`

Removes passed class from element's `className` attribute.

### Remove element from the DOM

`$myEl.remove()`

### Set a random background on element

```
$myEl.setRandomBackground({
  path: 'some/path',
  range: [0, 10],
  length: 3,
  ext: 'jpg'
})
 ```

Sets a background image with the following format:

`url(${path}/${name}.${ext})`

Where:
- `${path}` is the given `path`.
- `${name}` is a random number in the given range with the specified length.
- `${ext}` is the file extension, as passed on `ext`.

Default values:
- range: `[0, 5]`
- length: `3`
- ext: `jpg`

If we have the following files:

```
img/00100.jpg
img/00101.jpg
img/00102.jpg
img/00103.jpg
img/00104.jpg
img/00105.jpg
```

To randomly select a background image we should:

```
$myEl.setRandomBackground({
  path: 'img',
  range: [100, 105],
  length: 5
})
```

### Appear element

`$myEl.appear()`

Sets `opacity` to `1`.

### Disappear element

`$myEl.disappear()`

Sets `opacity` to `0`.

### Focus element

`$myEl.focus()`

### Set element's HTML

`$myEl.html('<strong>Rock it!</strong>')`

### Get element's HTML

`$myEl.html()`

### Append HTML to element

`$myEl.appendHtml('<i>Pizza!</i>')`

Adds passed HTML content at the end of the element.

### Prepend HTML to element

`$myEl.prependHtml('<b>Thanks to:</b>')`

Adds passed HTML content at the beggining of the element.

### Set value

`$myEl.val(42)`

Sets passed value as element's value.

Applies for inputs and textareas, but you can set a value on any element
even if it's not rendered.

### Get value

`$myEl.val()`

Returns current element's value.

### Clear value

`$myEl.clear()`

Sets element's value to an empty string.

### Is element visible?

`$myEl.isVisible()`

Returns true if the element's `display` CSS attribute is not set or one of:
- block
- inline
- inline-block

### Toggle element's visibility

`$myEl.toggle()`

Uses `$myEl.isVisible()` to detect visibility.

Calls `$myEl.show()` when element is hidden.

Calls `$myEl.hide()` when element is visible.

### Position caret at the end of an input's content

`$myEl.caretEnd()`

### Set element's src

`$myEl.src('img/groovy.jpg')`

Sets passed value on the `src` attribute.

### Get element's src

`$myEl.src()`

Returns current `src` value.

### Scroll to bottom

`$myEl.scrollBottom()`

Moves scroll position to the bottom of the element.

### Add event listener

`$myEl.on('click', () => console.log('clicked!'))`

Listen to element events passing a callback.

### Inject styles on page

`El.injectStyles(styles)`

Note that this is a static method that's called directly on the `El` object.

Example:

```
El.injectStyles(`
  body {
    background: black;
    color: white;
  }

  h1 {
    font-size: 48px;
  }
`)
```
