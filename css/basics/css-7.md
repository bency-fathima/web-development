# CSS Background

CSS provides various properties to control the background of elements, including color, images, and gradients.

---

## 1. `background-color`
Sets the background color of an element.
```css
background-color: lightblue;
```
You can use:
- Named colors (`red`, `blue`, etc.)
- Hex codes (`#ff0000`)
- RGB values (`rgb(255, 0, 0)`) 
- RGBA for transparency (`rgba(255, 0, 0, 0.5)`) 

---

## 2. `background-image`
Sets an image as the background.
```css
background-image: url("background.jpg");
```
To use a gradient:
```css
background-image: linear-gradient(to right, red, blue);
```

---

## 3. `background-size`
Defines the size of the background image.
```css
background-size: cover; /* Covers the entire element */
background-size: contain; /* Fits inside the element */
background-size: 100px 50px; /* Custom width and height */
```

---

## 4. `background-repeat`
Controls whether the background image repeats.
```css
background-repeat: repeat;    /* Default, repeats both directions */
background-repeat: no-repeat; /* No repetition */
background-repeat: repeat-x;  /* Repeats horizontally */
background-repeat: repeat-y;  /* Repeats vertically */
```

---

## 5. `background-position`
Sets the position of the background image.
```css
background-position: center; /* Centered */
background-position: top right; /* Positioned at the top-right */
background-position: 50px 100px; /* Custom position */
```

---

## 6. `background-attachment`
Defines if the background scrolls with the page.
```css
background-attachment: scroll; /* Default, moves with scrolling */
background-attachment: fixed;  /* Stays fixed while scrolling */
background-attachment: local;  /* Scrolls within the element */
```


 
---

## 9. `background` (Shorthand)
The `background` shorthand property allows you to set multiple background properties at once.
```css
background: lightblue url("image.jpg") no-repeat center/cover;
```
**Order:** `color` → `image` → `repeat` → `position/size` → `attachment`

---

## 10. Example

### HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Background Example</title>
    <style>
        .background-box {
            width: 300px;
            height: 200px;
            background: lightblue url("background.jpg") no-repeat center/cover;
            border: 2px solid black;
        }
    </style>
</head>
<body>
    <div class="background-box">This box has a background.</div>
</body>
</html>
```

### Explanation
- The `.background-box` has a background color and an image.
- The `no-repeat` prevents the image from repeating.
- `center/cover` ensures the image covers the box while staying centered.

---

## Conclusion
The CSS background properties provide powerful control over element backgrounds, allowing you to customize colors, images, and gradients efficiently.
