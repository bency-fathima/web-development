# CSS Padding

CSS padding is used to create space inside an element, between the content and its border.

---

## 1. The `padding` Property
The `padding` property defines the inner spacing of an element.
```css
padding: 20px;
```
This applies `20px` of padding to all sides (top, right, bottom, and left).

---

## 2. Individual Padding Properties
Padding can be set for each side separately:
```css
padding-top: 10px;
padding-right: 15px;
padding-bottom: 20px;
padding-left: 25px;
```

---

## 3. Padding Shorthand
The `padding` property can take up to four values:

### 3.1 Four Values (Top, Right, Bottom, Left)
```css
padding: 10px 15px 20px 25px;
```
- Top: `10px`
- Right: `15px`
- Bottom: `20px`
- Left: `25px`

### 3.2 Three Values (Top, Horizontal, Bottom)
```css
padding: 10px 15px 20px;
```
- Top: `10px`
- Left & Right: `15px`
- Bottom: `20px`

### 3.3 Two Values (Vertical, Horizontal)
```css
padding: 10px 15px;
```
- Top & Bottom: `10px`
- Left & Right: `15px`

### 3.4 One Value (All Sides)
```css
padding: 10px;
```
- All sides: `10px`

---

## 4. Padding and Box Model
Padding affects the size of an element. By default, the total width and height include only content, but padding increases the size unless `box-sizing: border-box;` is used.

### Example:
```css
div {
    width: 200px;
    padding: 20px;
    border: 2px solid black;
}
```
The total width becomes `200px + 20px (left) + 20px (right) = 240px`.

To include padding inside the width, use:
```css
div {
    box-sizing: border-box;
}
```

---

## 5. Percentage Padding
Padding can be set in percentages relative to the width of the containing element.
```css
padding: 10%;
```
This means `10%` of the parent element’s width.

---

## 6. Padding vs. Margin
- **Padding** adds space inside an element.
- **Margin** adds space outside an element.

Example:
```css
div {
    padding: 20px; /* Space inside the border */
    margin: 20px;  /* Space outside the border */
}
```
# CSS Height and Width Properties

CSS provides the `height` and `width` properties to control the size of elements.

## 1. The `width` Property
The `width` property sets the horizontal size of an element.
```css
width: 200px;
```
This sets the element’s width to `200px`.

### Width Values
- **Fixed (`px`)**: Defines an exact width.
  ```css
  width: 300px;
  ```
- **Percentage (`%`)**: Sets width relative to the parent element.
  ```css
  width: 50%;
  ```
- **Auto**: Adjusts width based on content.
  ```css
  width: auto;
  ```
- **Viewport Width (`vw`)**: Relative to the viewport’s width.
  ```css
  width: 50vw;
  ```

## 2. The `height` Property
The `height` property sets the vertical size of an element.
```css
height: 100px;
```
This sets the element’s height to `100px`.

### Height Values
- **Fixed (`px`)**: Defines an exact height.
  ```css
  height: 200px;
  ```
- **Percentage (`%`)**: Sets height relative to the parent element.
  ```css
  height: 50%;
  ```
- **Auto**: Adjusts height based on content.
  ```css
  height: auto;
  ```
- **Viewport Height (`vh`)**: Relative to the viewport’s height.
  ```css
  height: 50vh;
  ```

---

## Conclusion
CSS padding controls the space inside an element. It can be set individually or using shorthand, and it affects the element's size based on the box model.
