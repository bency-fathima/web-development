# CSS Margins

CSS margins are used to create space around elements, outside of their borders.

---

## 1. The `margin` Property
The `margin` property sets the margin space for all four sides of an element.
```css
margin: 20px;
```
This applies `20px` of margin on all sides (top, right, bottom, and left).

---

## 2. Individual Margin Properties
You can specify different margin values for each side:
```css
margin-top: 10px;
margin-right: 15px;
margin-bottom: 20px;
margin-left: 25px;
```

---

## 3. Margin Shorthand
You can use shorthand notation to define margins in a single line:

### 3.1 Four Values (Top, Right, Bottom, Left)
```css
margin: 10px 15px 20px 25px;
```
- Top: `10px`
- Right: `15px`
- Bottom: `20px`
- Left: `25px`

### 3.2 Three Values (Top, Horizontal, Bottom)
```css
margin: 10px 15px 20px;
```
- Top: `10px`
- Left & Right: `15px`
- Bottom: `20px`

### 3.3 Two Values (Vertical, Horizontal)
```css
margin: 10px 15px;
```
- Top & Bottom: `10px`
- Left & Right: `15px`

### 3.4 One Value (All Sides)
```css
margin: 10px;
```
- All sides: `10px`

---

## 4. Auto Margin
Using `margin: auto;` centers an element horizontally inside its parent if it has a specified width.
```css
div {
    width: 50%;
    margin: auto;
}
```

---

## 5. Margin Collapse
Margins of adjacent elements can collapse into a single margin instead of adding up.

### Example:
```css
div {
    margin-bottom: 20px;
}
p {
    margin-top: 30px;
}
```
If a `<div>` has `margin-bottom: 20px;` and a `<p>` has `margin-top: 30px;`, the final margin between them will be `30px`, not `50px` (whichever is larger).

---

## 6. Negative Margins
Negative values are allowed and can pull an element closer to its neighbors.
```css
margin-top: -10px;
margin-left: -5px;
```

---

## Conclusion
CSS margins help control the spacing between elements. Understanding margin properties, shorthand, auto-centering, and margin collapse can help improve layout design and spacing in web development.
