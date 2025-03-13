# Cascading Style Sheets (CSS)

## What is CSS?
CSS stands for Cascading Style Sheets and is used to style and layout web pages.
CSS is a stylesheet language used to control the presentation and layout of HTML documents. It allows developers to apply styles such as colors, fonts, spacing, and positioning to web pages, ensuring a consistent and visually appealing design.

# 📖 What Does CSS Do?

CSS enhances the appearance of web pages by allowing you to:

- **Change Colors** – Apply different colors to text, backgrounds, and borders.
- **Modify Fonts** – Set font type, size, style, and weight.
- **Control Layout** – Adjust the positioning of elements (flexbox, grid, etc.).
- **Add Spacing** – Define margins, padding, and borders for better spacing.
- **Responsive Design** – Make web pages look good on all screen sizes (mobile, tablet, desktop).
- **Animation and Effects** – Create transitions, animations, and hover effects.



 # CSS Basics

CSS (Cascading Style Sheets) is used to style HTML elements. There are three main ways to apply CSS to a webpage:

## 1. Inline CSS
Inline CSS applies styles directly to an HTML element using the `style` attribute.

```html
<p style="color: blue; font-size: 16px;">This is an inline-styled paragraph.</p>
```

### Pros:
- Quick and easy for small changes.
- Does not require an external file.

### Cons:
- Hard to maintain and scale.
- Can clutter HTML code.

## 2. Internal CSS
Internal CSS is defined within a `<style>` tag inside the `<head>` section of an HTML document.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Internal CSS Example</title>
    <style>
        p {
            color: green;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <p>This paragraph is styled using internal CSS.</p>
</body>
</html>
```

### Pros:
- Keeps CSS in the same file as HTML.
- Good for single-page projects.

### Cons:
- Not reusable across multiple pages.
- Can become unmanageable in large projects.

## 3. External CSS
External CSS is written in a separate `.css` file and linked to the HTML file using a `<link>` tag.

### CSS File (`styles.css`)
```css
p {
    color: red;
    font-size: 20px;
}
```

### HTML File
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>External CSS Example</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <p>This paragraph is styled using external CSS.</p>
</body>
</html>
```

### Pros:
- Keeps styling separate from HTML for better readability and maintainability.
- Reusable across multiple pages.

### Cons:
- Requires an additional HTTP request to load the CSS file.
- Not ideal for small, one-page projects.

## Conclusion
Each CSS styling method has its use case. For large projects, external CSS is recommended for maintainability. Internal CSS is useful for quick, single-page applications, while inline CSS should generally be avoided except for special cases like email templates or dynamic styling with JavaScript.
