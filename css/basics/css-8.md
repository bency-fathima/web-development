# CSS Positioning and Display Properties

## Introduction
CSS provides various positioning and display properties to control how elements are placed and rendered on a webpage. Understanding these properties is essential for creating structured and responsive layouts.

## 1. CSS Positioning
The `position` property determines how an element is positioned in the document.

### 1.1 Static Positioning (Default)
By default, all elements are positioned as `static`, which means they follow the normal document flow.
```css
.box {
    position: static;
}
```

### 1.2 Relative Positioning
A `relative` positioned element moves relative to its normal position.
```css
.box {
    position: relative;
    top: 20px; /* Moves 20px down from original position */
    left: 10px; /* Moves 10px right from original position */
}
```

### 1.3 Absolute Positioning
An `absolute` positioned element is removed from the normal document flow and positioned relative to its nearest positioned ancestor (not `static`).
```css
.box {
    position: absolute;
    top: 50px;
    left: 100px;
}
```

### 1.4 Fixed Positioning
A `fixed` positioned element is removed from the document flow and stays in place relative to the viewport, even when scrolling.
```css
.box {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    background-color: black;
}
```

### 1.5 Sticky Positioning
A `sticky` positioned element toggles between `relative` and `fixed`, depending on scroll position.
```css
.box {
    position: sticky;
    top: 10px; /* Sticks when scrolling past 10px */
}
```

## 2. CSS Display Property
The `display` property controls how elements are displayed on the page.

### 2.1 Block Elements
Block-level elements take up the full width of their container and start on a new line.
```css
div {
    display: block;
}
```

### 2.2 Inline Elements
Inline elements only take up as much width as needed and do not start on a new line.
```css
span {
    display: inline;
}
```

### 2.3 Inline-Block Elements
`inline-block` elements behave like inline elements but respect width and height properties.
```css
.box {
    display: inline-block;
    width: 100px;
    height: 50px;
}
```

### 2.4 None (Hiding Elements)
Setting `display: none;` removes the element from the document flow.
```css
.box {
    display: none;
}
```

## 3. Flexbox and Grid (Advanced Layouts)
For better control over layouts, `flexbox` and `grid` provide modern solutions.

### 3.1 Flexbox Example
```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

### 3.2 Grid Example
```css
.container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
}
```

## Conclusion
Understanding positioning and display properties helps in structuring web layouts effectively. Using combinations of these properties allows for dynamic and responsive designs.

---
**Next Steps:**
- Explore `z-index` for stacking elements.
- Learn advanced Flexbox and Grid techniques.
- Experiment with real-world layouts using positioning and display properties.
