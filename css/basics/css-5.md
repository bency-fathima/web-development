# CSS Specificity and Inheritance

## Introduction
Understanding CSS specificity and inheritance is crucial for writing efficient styles and avoiding conflicts in your stylesheets. Specificity determines which styles apply when multiple rules target the same element, while inheritance allows certain properties to be passed down from parent elements to child elements.

## 1. CSS Specificity
Specificity is the priority given to CSS rules when multiple rules apply to the same element. It is calculated based on the type of selectors used.

### Specificity Calculation
CSS assigns a numerical weight to different selector types:
- **Inline styles** (`style=""`) → `1000`
- **ID selectors** (`#id`) → `100`
- **Class, attribute, and pseudo-class selectors** (`.class`, `[attribute]`, `:hover`) → `10`
- **Element and pseudo-element selectors** (`div`, `p`, `::before`) → `1`
- **Universal selector (`*`) and combinators (`+`, `>`, `~`)** → `0`

### Example Specificity Calculation
```css
/* Specificity: 1 (element selector) */
p {
    color: blue;
}

/* Specificity: 10 (class selector) */
.highlight {
    color: red;
}

/* Specificity: 100 (ID selector) */
#main-text {
    color: green;
}

/* Specificity: 1000 (inline style) */
<p style="color: orange;">This has highest priority.</p>
```
### How Specificity Works
If multiple rules apply to the same element, the rule with the highest specificity wins. Inline styles have the highest priority, followed by ID selectors, class selectors, and element selectors.

## 2. CSS Inheritance
Inheritance allows child elements to inherit certain properties from their parent elements. However, not all properties are inherited by default.

### Inherited Properties
Properties related to **text and fonts** are typically inherited:
```css
body {
    font-family: Arial, sans-serif;
    color: blue;
}
```
All child elements inside `<body>` will inherit the `font-family` and `color` properties unless overridden.

### Non-Inherited Properties
Properties related to **box model, layout, and spacing** (e.g., `margin`, `padding`, `border`, `width`, etc.) are not inherited by default.
```css
body {
    margin: 20px; /* NOT inherited by child elements */
}
```

### Controlling Inheritance
- **Force inheritance** with `inherit`:
```css
p {
    color: inherit;
}
```
- **Prevent inheritance** with `initial` (resets to default value):
```css
p {
    color: initial;
}
```
- **Use `unset`** (resets inherited properties to inherit and non-inherited properties to initial):
```css
p {
    color: unset;
}
```

## 3. Combining Specificity and Inheritance
- Specificity determines which rule applies when there are conflicting styles.
- Inheritance ensures child elements receive appropriate styling unless overridden by a more specific rule.

### Example:
```css
body {
    font-family: Arial, sans-serif;
}

p {
    color: red; /* Applied because text properties are inherited */
}

.highlighted {
    color: green; /* More specific (class selector, specificity: 10) */
}
```

## Conclusion
Understanding CSS specificity and inheritance helps in structuring styles effectively and avoiding unnecessary overrides. By using proper specificity, inheritance, and best practices, you can maintain clean and manageable stylesheets.

---
**Next Steps:**
- Experiment with specificity using different selector combinations.
- Learn about the `!important` rule and when to use it (sparingly).
- Explore advanced selector strategies like nesting with pre-processors (SASS/SCSS).
