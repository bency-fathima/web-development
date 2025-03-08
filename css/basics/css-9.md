# CSS List Styling

CSS provides various properties to style lists, including changing bullet styles, positioning, and customizing list appearance.

---

## 1. `list-style-type`
Defines the type of bullet points or numbering for lists.

### Example:
```css
ul {
    list-style-type: square; /* Options: disc, circle, square, none */
}

ol {
    list-style-type: upper-roman; /* Options: decimal, lower-alpha, upper-alpha, lower-roman, upper-roman */
}
```

### Common Values:
- **Unordered Lists (`<ul>`)**:
  - `disc` (default) ●
  - `circle` ○
  - `square` ■
  - `none` (removes bullets)
- **Ordered Lists (`<ol>`)**:
  - `decimal` (default) 1, 2, 3…
  - `lower-alpha` a, b, c…
  - `upper-alpha` A, B, C…
  - `lower-roman` i, ii, iii…
  - `upper-roman` I, II, III…

---

## 2. `list-style-position`
Defines whether bullets/numbers appear inside or outside the list item.

### Example:
```css
ul {
    list-style-position: inside; /* Options: inside, outside (default) */
}
```

### Differences:
- **`inside`**: Bullets align with text.
- **`outside`**: Bullets appear outside the text block (default).

---

## 3. `list-style-image`
Replaces bullets with an image.

### Example:
```css
ul {
    list-style-image: url("bullet.png");
}
```

---

## 4. `list-style` (Shorthand)
Combines `list-style-type`, `list-style-position`, and `list-style-image`.

### Example:
```css
ul {
    list-style: square inside url("bullet.png");
}
```

---

## 5. Removing Default List Styles
To remove bullets or numbering from a list:
```css
ul, ol {
    list-style: none;
    padding: 0;
    margin: 0;
}
```
This is useful for navigation menus.

---

## 6. Styling List Items
List items (`<li>`) can be styled like any other element.
```css
li {
    color: blue;
    font-weight: bold;
    margin-bottom: 10px;
}
```

---

## 7. Example: Custom Styled List

### HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS List Styling Example</title>
    <style>
        ul {
            list-style: square inside;
            padding-left: 20px;
        }
        ol {
            list-style-type: upper-roman;
            list-style-position: outside;
        }
        li {
            color: darkblue;
            font-size: 18px;
            margin-bottom: 5px;
        }
    </style>
</head>
<body>
    <h2>Unordered List</h2>
    <ul>
        <li>Item One</li>
        <li>Item Two</li>
        <li>Item Three</li>
    </ul>
    
    <h2>Ordered List</h2>
    <ol>
        <li>First</li>
        <li>Second</li>
        <li>Third</li>
    </ol>
</body>
</html>
```

### Explanation:
- The unordered list (`<ul>`) uses `square` bullets inside the text.
- The ordered list (`<ol>`) uses `upper-roman` numbers.
- List items (`<li>`) are styled with dark blue color and increased font size.

---

## Conclusion
CSS list styling allows you to modify bullet types, numbering, positioning, and even use images for list markers. Proper styling makes lists visually appealing and improves readability.
