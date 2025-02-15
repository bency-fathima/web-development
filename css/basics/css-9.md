# Font Styling Using CSS and Web Safe Fonts

## Introduction
Font styling in CSS allows you to control text appearance, improving readability and aesthetics. CSS provides various properties for customizing fonts, including font family, size, weight, style, and more.

## 1. Font Family
The `font-family` property defines the typeface used for text. Web-safe fonts ensure that text displays consistently across different devices and browsers.

### Example:
```css
body {
    font-family: Arial, sans-serif;
}
```

### Web-Safe Fonts:
- **Serif:** Times New Roman, Georgia, Garamond
- **Sans-Serif:** Arial, Helvetica, Verdana
- **Monospace:** Courier New, Consolas, Monaco
- **Cursive:** Brush Script MT, Comic Sans MS
- **Fantasy:** Impact, Papyrus

## 2. Font Size
The `font-size` property controls text size. Common units include:
- **px (pixels)** – Fixed size.
- **em** – Relative to parent element.
- **rem** – Relative to the root element (`html`).
- **%** – Relative to parent element’s font size.

### Example:
```css
p {
    font-size: 16px;
}
```

## 3. Font Weight
The `font-weight` property specifies how bold the text appears. Values include:
- `normal`
- `bold`
- `lighter`
- `bolder`
- Numeric values (`100` to `900`)

### Example:
```css
h1 {
    font-weight: bold;
}
```

## 4. Font Style
The `font-style` property changes the appearance of text, commonly used for italics.

### Example:
```css
em {
    font-style: italic;
}
```

## 5. Text Transform
The `text-transform` property changes the text capitalization.

### Example:
```css
h2 {
    text-transform: uppercase;
}
```

## 6. Text Decoration
The `text-decoration` property adds effects like underlining or strikethrough.

### Example:
```css
a {
    text-decoration: none;
}
```

## 7. Line Height and Letter Spacing
- `line-height`: Controls spacing between lines.
- `letter-spacing`: Adjusts spacing between characters.

### Example:
```css
p {
    line-height: 1.5;
    letter-spacing: 0.05em;
}
```

## 8. Google Fonts and Custom Fonts
Using Google Fonts allows access to various web fonts.

### Example (Google Fonts):
```html
<head>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
</head>
```
```css
body {
    font-family: 'Roboto', sans-serif;
}
```

## Conclusion
Font styling enhances the readability and aesthetic appeal of websites. Using web-safe fonts and external font sources ensures consistency across devices.

---
**Next Steps:**
- Experiment with different font styles and families.
- Learn about variable fonts for better performance.
- Explore responsive typography techniques using media queries.
