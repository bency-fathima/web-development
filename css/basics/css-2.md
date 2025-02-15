# CSS Selectors and Properties

## CSS Selectors
CSS selectors are patterns used to select and style HTML elements. Here are some common types:

### 1. Universal Selector (`*`)
Selects all elements on a page.
```css
* {
    margin: 0;
    padding: 0;
}
```

### 2. Element Selector
Selects all elements of a specific type.
```css
p {
    color: blue;
}
```

### 3. Class Selector (`.`)
Selects all elements with a specific class.
```css
.highlight {
    background-color: yellow;
}
```

### 4. ID Selector (`#`)
Selects a single element with a specific ID.
```css
#main-heading {
    font-size: 24px;
}
```

### 5. Group Selector
Selects multiple elements at once.
```css
h1, h2, p {
    font-family: Arial, sans-serif;
}
```

### 6. Descendant Selector
Selects elements inside a specific element.
```css
div p {
    color: green;
}
```

### 7. Child Selector (`>`)
Selects direct children of an element.
```css
div > p {
    color: red;
}
```

 

## CSS Properties
CSS properties define the appearance of elements. Here are some fundamental properties:

### 1. Color and Background
```css
color: red; /* Text color */
background-color: yellow; /* Background color */
```

### 2. Font and Text Styling
```css
font-size: 16px;
font-family: Arial, sans-serif;
font-weight: bold;
text-align: center;
```

### 3. Box Model
```css
margin: 10px; /* Space outside element */
padding: 10px; /* Space inside element */
border: 1px solid black;
```

### 4. Display and Positioning
```css
display: flex;
position: absolute;
top: 50px;
left: 100px;
```

### 5. Flexbox and Grid
```css
display: flex;
justify-content: center;
align-items: center;
```
```css
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 10px;
```

## Conclusion
CSS selectors and properties are essential for styling web pages. Understanding these fundamentals will help you design more structured and visually appealing websites.

---
**Next Steps**:
- Explore advanced selectors like `nth-child` and `not`.
- Learn about responsive design with media queries.
- Practice with real-world CSS challenges!
