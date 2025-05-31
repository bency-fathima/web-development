
# CSS Media Queries

**Media Queries** in CSS are used to apply styles based on the device's characteristics such as screen width, height, resolution, and orientation.

They help in creating **responsive designs** that work across various devices (mobile, tablet, desktop).

---

## Basic Syntax

```css
@media media-type and (condition) {
  /* CSS rules here */
}
```

- `media-type` (optional): e.g., `screen`, `print`, `all`
- `condition`: a feature like `max-width`, `min-width`, etc.

---

## Common Examples

### 1. Target screens smaller than 600px

```css
@media (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
```

### 2. Target screens larger than 768px

```css
@media (min-width: 768px) {
  .container {
    padding: 40px;
  }
}
```

### 3. Target between 768px and 1024px

```css
@media (min-width: 768px) and (max-width: 1024px) {
  .menu {
    font-size: 18px;
  }
}
```

### 4. Orientation: Landscape

```css
@media (orientation: landscape) {
  .banner {
    height: 200px;
  }
}
```

---

## Tips

- Always use **mobile-first** approach: write base styles for mobile, then use `min-width` queries for larger screens.
- Group related media queries together for readability.
- Test on real devices or use responsive tools in browser dev tools.

---

