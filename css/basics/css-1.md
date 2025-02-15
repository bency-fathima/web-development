# Cascading Style Sheets (CSS)

## What is CSS?
Cascading Style Sheets (CSS) is a stylesheet language used to control the presentation and layout of HTML documents. It allows developers to apply styles such as colors, fonts, spacing, and positioning to web pages, ensuring a consistent and visually appealing design.

## Why Use CSS?
- **Separation of Content and Design**: Keeps HTML structure clean and improves maintainability.
- **Consistency**: Ensures uniform styling across multiple pages.
- **Responsive Design**: Helps create layouts that adapt to different screen sizes.
- **Improved Performance**: Reduces redundancy and page load time.

## How to Use CSS
There are three main ways to apply CSS to a webpage:

### 1. Inline CSS
CSS can be applied directly within an HTML element using the `style` attribute.
```html
<p style="color: blue; font-size: 16px;">This is a styled paragraph.</p>
```

### 2. Internal CSS
Defined within a `<style>` tag inside the `<head>` section of an HTML document.
```html
<head>
    <style>
        p {
            color: blue;
            font-size: 16px;
        }
    </style>
</head>
```

### 3. External CSS
A separate CSS file is linked to the HTML document using the `<link>` tag.
```html
<head>
    <link rel="stylesheet" href="styles.css">
</head>
```
Example `styles.css` file:
```css
p {
    color: blue;
    font-size: 16px;
}
```

## CSS Selectors
CSS uses selectors to target HTML elements for styling. Some common types include:
- **Element Selector**: Targets all instances of an element.
  ```css
  p {
      color: red;
  }
  ```
- **Class Selector**: Targets elements with a specific class.
  ```css
  .highlight {
      background-color: yellow;
  }
  ```
- **ID Selector**: Targets a single element with a specific ID.
  ```css
  #main-heading {
      font-size: 24px;
  }
  ```
- **Group Selector**: Targets multiple elements.
  ```css
  h1, h2, p {
      font-family: Arial, sans-serif;
  }
  ```

## The Cascade in CSS
CSS follows a cascading priority system:
1. **Inline styles** (highest priority)
2. **Internal styles** (within `<style>` tags)
3. **External stylesheets**
4. **Browser default styles** (lowest priority)

## Conclusion
CSS is an essential tool for web development that allows for flexible and efficient styling of websites. By understanding its different applications and principles, you can create visually appealing and user-friendly web pages.

---
**Next Steps**:
- Learn about **CSS Flexbox** and **CSS Grid** for layout design.
- Explore **CSS animations** and **transitions**.
- Practice with real-world projects!
