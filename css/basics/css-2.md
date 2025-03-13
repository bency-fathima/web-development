# CSS Selectors and Properties

## CSS Selectors
CSS selectors are used to target HTML elements and apply styles to them. Below are some common types of selectors:



### 1. Element Selector
Targets a specific HTML element.
```css
p {
    color: blue;
}
```

### 2. Class Selector (`.`)
Targets elements with a specific class.
```css
.my-class {
    font-size: 18px;
}
```
Usage in HTML:
```html
<p class="my-class">This is a styled paragraph.</p>
```

### 3. ID Selector (`#`)
Targets a specific element with an ID.
```css
#unique-id {
    background-color: yellow;
}
```
Usage in HTML:
```html
<div id="unique-id">This is a unique element.</div>
```


  ### . Universal Selector (`*`)
Applies styles to all elements.
```css
* {
    margin: 0;
    padding: 0;
}
```
