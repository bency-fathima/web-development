# CSS Overflow

The `overflow` property in CSS controls how content behaves when it exceeds the size of its container.

---

## 1. `overflow` Property
Defines how overflowing content is handled.
```css
overflow: visible; /* Default: content overflows outside */
overflow: hidden;  /* Hides overflowed content */
overflow: scroll;  /* Adds scrollbars when content overflows */
overflow: auto;    /* Adds scrollbars only when needed */
```

---

## 2. `overflow-x` and `overflow-y`
Controls overflow separately for horizontal (`x`) and vertical (`y`) directions.
```css
overflow-x: hidden; /* Hides horizontal overflow */
overflow-y: scroll; /* Adds vertical scrollbar */
```

---

## 3. Example: Controlling Overflow

### HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Overflow Example</title>
    <style>
        .box {
            width: 200px;
            height: 100px;
            border: 2px solid black;
            overflow: auto;
        }
    </style>
</head>
<body>
    <div class="box">
        This is a box with overflowing text. If the content is too large, scrollbars will appear as needed.
    </div>
</body>
</html>
```

### Explanation:
- The `.box` is `200px` wide and `100px` tall.
- `overflow: auto;` adds scrollbars only when content overflows.
- Users can scroll inside the box when necessary.

---

## 4. `overflow: hidden;` Example
Hides overflow without scrollbars.
```css
.box {
    width: 200px;
    height: 100px;
    overflow: hidden;
}
```

---

## 5. `overflow: scroll;` Example
Forces scrollbars, even if content fits.
```css
.box {
    width: 200px;
    height: 100px;
    overflow: scroll;
}
```

---

## Conclusion
The `overflow` property manages how content behaves when it exceeds its container’s dimensions. Using `hidden`, `scroll`, or `auto` ensures better user experience and layout control.
