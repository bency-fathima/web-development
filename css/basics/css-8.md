# CSS Text Properties

CSS provides various properties to control the appearance and alignment of text.

---

## 1. `color`
Sets the color of the text.
```css
color: red;
```
Supports named colors, hex codes, RGB, and HSL values.
```css
color: #ff0000;  /* Hex */
color: rgb(255, 0, 0);  /* RGB */
color: hsl(0, 100%, 50%);  /* HSL */
```

---

## 2. `text-align`
Aligns the text inside an element.
```css
text-align: left;   /* Aligns text to the left */
text-align: right;  /* Aligns text to the right */
text-align: center; /* Centers text */
text-align: justify; /* Stretches text to fill width */
```

---

## 3. `text-decoration`
Adds visual decorations to text.
```css
text-decoration: none;       /* Removes decoration */
text-decoration: underline;  /* Underlines text */
text-decoration: overline;   /* Adds a line above text */
text-decoration: line-through; /* Strikethrough text */
```

---

## 4. `text-transform`
Controls text capitalization.
```css
text-transform: uppercase;  /* Converts text to uppercase */
text-transform: lowercase;  /* Converts text to lowercase */
text-transform: capitalize; /* Capitalizes first letter of each word */
```

---

## 5. `letter-spacing`
Adjusts spacing between characters.
```css
letter-spacing: 2px;  /* Increases space */
letter-spacing: -1px; /* Decreases space */
```

---

## 6. `word-spacing`
Adjusts spacing between words.
```css
word-spacing: 5px;
```

---

## 7. `line-height`
Controls the space between lines of text.
```css
line-height: 1.5; /* 1.5 times the font size */
line-height: 20px; /* Fixed value */
```

---

## 8. `white-space`
Defines how white space is handled.
```css
white-space: normal;  /* Default, collapses spaces */
white-space: nowrap;  /* Prevents text wrapping */
white-space: pre;     /* Preserves spaces and line breaks */
```

---

## 9. `text-shadow`
Adds a shadow effect to text.
```css
text-shadow: 2px 2px 5px gray;  /* X-offset, Y-offset, blur-radius, color */
```

---

## 10. Example

### HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Text Example</title>
    <style>
        .styled-text {
            color: blue;
            text-align: center;
            text-decoration: underline;
            text-transform: uppercase;
            letter-spacing: 2px;
            line-height: 1.5;
            text-shadow: 2px 2px 5px gray;
        }
    </style>
</head>
<body>
    <p class="styled-text">This is styled text.</p>
</body>
</html>
```

### Explanation
- The `.styled-text` class applies multiple text properties.
- `color: blue;` changes text color.
- `text-align: center;` centers the text.
- `text-decoration: underline;` underlines the text.
- `text-transform: uppercase;` converts text to uppercase.
- `letter-spacing: 2px;` increases spacing between letters.
- `line-height: 1.5;` increases space between lines.
- `text-shadow: 2px 2px 5px gray;` adds a shadow effect.

---

## Conclusion
CSS text properties allow you to control text alignment, decoration, spacing, and effects, enhancing readability and design.
