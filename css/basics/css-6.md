# CSS Outline

The CSS `outline` property is used to draw a line outside the element’s border without taking up space in the layout.

---

## 1. The `outline` Property
The `outline` property is a shorthand for setting the outline width, style, and color.
```css
outline: 2px solid red;
```
This creates a `2px` solid red outline around the element.

---

## 2. Individual Outline Properties

### `outline-width`
Specifies the thickness of the outline.
```css
outline-width: 5px;
```

### `outline-style`
Defines the appearance of the outline.
```css
outline-style: solid;    /* Solid line */
outline-style: dashed;   /* Dashed line */
outline-style: dotted;   /* Dotted line */
outline-style: double;   /* Double line */
outline-style: groove;   /* 3D groove effect */
outline-style: ridge;    /* 3D ridge effect */
outline-style: inset;    /* 3D inset effect */
outline-style: outset;   /* 3D outset effect */
outline-style: none;     /* No outline */
```

### `outline-color`
Sets the color of the outline.
```css
outline-color: blue;
```
Or use transparency:
```css
outline-color: rgba(255, 0, 0, 0.5);
```

---

## 3. Outline Offset
The `outline-offset` property adds space between the outline and the element’s border.
```css
outline-offset: 10px;
```
This moves the outline `10px` away from the element’s border.

---

## 4. Example: Highlighting an Element

### HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Outline Example</title>
    <style>
        .outlined-box {
            width: 200px;
            padding: 20px;
            border: 2px solid black;
            outline: 4px dashed red;
            outline-offset: 5px;
            background-color: lightgray;
        }
    </style>
</head>
<body>
    <div class="outlined-box">This box has an outline.</div>
</body>
</html>
```

### Explanation
- The `.outlined-box` has a `4px` dashed red outline.
- The `outline-offset: 5px;` pushes the outline away from the border.
- The background color makes the outline stand out.

---

## 5. Outline vs. Border
- **Border** is part of the element’s box model and affects layout.
- **Outline** does not take up space and can be drawn outside the element.

Example:
```css
div {
    border: 3px solid blue; /* Affects layout */
    outline: 3px solid red; /* Does not affect layout */
}
```

---

## Conclusion
The `outline` property helps highlight elements without affecting their size or position. The `outline-offset` property allows further customization by controlling the distance between the element and its outline.
