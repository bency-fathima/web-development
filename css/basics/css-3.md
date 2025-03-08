# CSS Borders

CSS borders are used to define the outline of an HTML element. Borders can have different styles, widths, and colors.

## 1. Basic Border Properties

### `border`
The `border` property is a shorthand for setting the width, style, and color of a border.
```css
border: 2px solid black;
```

### `border-width`
Defines the thickness of the border.
```css
border-width: 5px;
```

### `border-style`
Defines the appearance of the border.

#### Common Border Styles:
```css
border-style: solid;    /* Solid line */
border-style: dashed;   /* Dashed line */
border-style: dotted;   /* Dotted line */
border-style: double;   /* Double line */
border-style: groove;   /* 3D groove effect */
border-style: ridge;    /* 3D ridge effect */
border-style: inset;    /* 3D inset effect */
border-style: outset;   /* 3D outset effect */
border-style: none;     /* No border */
```

### `border-color`
Sets the color of the border.
```css
border-color: red;
```

---

## 2. Individual Border Sides
You can apply borders to specific sides of an element:
```css
border-top: 3px solid blue;
border-right: 4px dashed green;
border-bottom: 5px double red;
border-left: 2px dotted purple;
```

---

## 3. Rounded Borders (`border-radius`)
The `border-radius` property creates rounded corners.
```css
border-radius: 10px;
```
You can specify different values for each corner:
```css
border-top-left-radius: 20px;
border-top-right-radius: 10px;
border-bottom-right-radius: 30px;
border-bottom-left-radius: 5px;
```

For circular borders, use `50%`:
```css
border-radius: 50%;
```

---

## 4. Border Shorthand
You can combine `border-width`, `border-style`, and `border-color` in a single declaration.
```css
border: 4px dotted blue;
```
For individual sides:
```css
border-top: 2px solid black;
border-right: 3px dashed red;
```

---

## 5. Border Images (`border-image`)
The `border-image` property allows using images as borders.
```css
border-image: url("border.png") 30 round;
```

Example with `border-image-source` and `border-image-slice`:
```css
border-image-source: url("border.png");
border-image-slice: 20;
border-image-repeat: stretch;
```

---

## Conclusion
CSS borders allow you to enhance the appearance of elements by defining their outlines with various styles, colors, and widths. Combining borders with `border-radius` and `border-image` can create visually appealing designs.
