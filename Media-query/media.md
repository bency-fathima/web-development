# 📱 Complete Guide to CSS Media Queries  

## 🔍 What is a Media Query?
A **media query** is a CSS technique used to apply styles depending on the **device’s characteristics** like screen size, resolution, orientation, color scheme, and more. It allows your design to **adapt responsively** to different devices and screen sizes.

**Syntax:**
```css
@media media-type and (condition) {
  /* CSS rules */
}
```

**Example:**
```css
@media screen and (max-width: 768px) {
  body {
    background-color: lightblue;
  }
}
```

---

## 🧠 Media Types
| Media Type | Description |
|------------|-------------|
| `all`      | Applies to all devices |
| `screen`   | Intended for screens (e.g. computers, tablets, smartphones) |
| `print`    | Intended for print preview mode and print devices |
| `speech`   | Intended for screen readers that read out loud |

---

## 🔧 Media Features
| Feature              | Description                                 |
|----------------------|---------------------------------------------|
| `width`              | Width of the viewport                       |
| `min-width`          | Minimum width of the viewport               |
| `max-width`          | Maximum width of the viewport               |
| `height`             | Height of the viewport                      |
| `min-height`         | Minimum height of the viewport              |
| `max-height`         | Maximum height of the viewport              |
| `orientation`        | Detects screen orientation (`portrait` or `landscape`) |
| `aspect-ratio`       | Ratio of width to height (e.g. 16/9)        |
| `resolution`         | Screen resolution (dpi, dppx)               |
| `hover`              | Detects if device can hover over elements   |
| `pointer`            | Quality of the pointing device (e.g., coarse, fine) |
| `prefers-color-scheme` | Detects user’s preferred color theme       |
| `prefers-reduced-motion` | Detects if user prefers less motion       |

---

## 🎯 Media Query Strategies

### ✅ Mobile-First Design (Recommended)
Start with base styles for mobile and add styles for larger screens:
```css
/* Base (mobile) styles */
body {
  font-size: 16px;
}

/* Tablet */
@media (min-width: 768px) {
  body {
    font-size: 18px;
  }
}

/* Desktop */
@media (min-width: 1024px) {
  body {
    font-size: 20px;
  }
}
```

### ❌ Desktop-First (Less common)
Start with large screens and use `max-width` for smaller sizes.
```css
body {
  font-size: 20px;
}

@media (max-width: 1023px) {
  body {
    font-size: 18px;
  }
}

@media (max-width: 767px) {
  body {
    font-size: 16px;
  }
}
```

---

## 📐 Common Breakpoints (Guideline)

| Device       | Breakpoint Range     |
|--------------|----------------------|
| Mobile       | 0px – 767px          |
| Tablet       | 768px – 1023px       |
| Laptop       | 1024px – 1439px      |
| Desktop      | 1440px and up        |

**Example:**
```css
@media (max-width: 767px) { }
@media (min-width: 768px) and (max-width: 1023px) { }
@media (min-width: 1024px) { }
```

---

## 📱 Orientation
```css
@media (orientation: landscape) {
  .layout {
    flex-direction: row;
  }
}

@media (orientation: portrait) {
  .layout {
    flex-direction: column;
  }
}
```

---

## 🌙 Dark Mode Support
```css
@media (prefers-color-scheme: dark) {
  body {
    background: #121212;
    color: white;
  }
}
```

---

## ✂️ Reduced Motion
```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation: none !important;
    transition: none !important;
  }
}
```

---

## 🔄 Logical Operators in Media Queries

### AND (`and`)
```css
@media screen and (min-width: 600px) and (orientation: landscape) { }
```

### OR (`,` as separator)
```css
@media screen and (max-width: 600px), (orientation: portrait) { }
```

### NOT (`not`)
```css
@media not screen and (min-width: 768px) {
  /* Applies to screens smaller than 768px */
}
```

---

## 🧠 Best Practices
- ✅ Always test on real devices and responsive mode in browsers
- ✅ Use relative units (`em`, `rem`) over `px` for breakpoints
- ✅ Keep breakpoints in a separate file if project is large
- ✅ Minimize the number of breakpoints—target major layout changes only
- ✅ Use `min-width` (mobile-first) for better scalability

---

## 📄 Full Example
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Responsive Example</title>
  <style>
    body {
      font-family: sans-serif;
      margin: 0;
      padding: 1rem;
      transition: all 0.3s ease-in-out;
    }
    .container {
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }

    @media (min-width: 768px) {
      .container {
        flex-direction: row;
      }
    }

    @media (prefers-color-scheme: dark) {
      body {
        background-color: #333;
        color: white;
      }
    }

    @media (orientation: landscape) {
      .container {
        border: 2px dashed blue;
      }
    }
  </style>
</head>
<body>
  <h1>Responsive Design with Media Queries</h1>
  <div class="container">
    <div style="flex: 1; background: #ccc; padding: 1rem;">Column 1</div>
    <div style="flex: 1; background: #eee; padding: 1rem;">Column 2</div>
  </div>
</body>
</html>
```

---

This comprehensive guide gives you everything you need to master **CSS media queries** and build responsive, accessible websites for any device or user preference.

