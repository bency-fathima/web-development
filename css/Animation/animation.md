
# CSS Animations

CSS Animations allow you to animate transitions from one CSS style to another. You can control animation timing, duration, and keyframes.

---

## Basic Syntax

```css
selector {
  animation-name: slidein;
  animation-duration: 3s;
  animation-timing-function: ease-in-out;
  animation-delay: 0s;
  animation-iteration-count: infinite;
  animation-direction: alternate;
}
```

- `animation-name`: Name of the keyframes rule
- `animation-duration`: How long the animation takes
- `animation-timing-function`: Acceleration curve (e.g., linear, ease, ease-in, ease-out)
- `animation-delay`: Wait time before animation starts
- `animation-iteration-count`: How many times to play (e.g., `infinite`, `1`, `3`)
- `animation-direction`: Direction of animation (e.g., `normal`, `alternate`, `reverse`)

---

## Defining Keyframes

```css
@keyframes slidein {
  from {
    transform: translateX(-100%);
  }
  to {
    transform: translateX(0);
  }
}
```

---

## Example: Sliding Box

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <style>
    .box {
      width: 100px;
      height: 100px;
      background-color: red;
      animation-name: slidein;
      animation-duration: 2s;
      animation-iteration-count: infinite;
      animation-direction: alternate;
    }

    @keyframes slidein {
      from {
        transform: translateX(0);
      }
      to {
        transform: translateX(300px);
      }
    }
  </style>
</head>
<body>
  <div class="box"></div>
</body>
</html>
```

---

## Shorthand Property

```css
animation: slidein 3s ease-in-out 1s infinite alternate;
```

---

## Tips

- Use `@keyframes` to define the animation steps.
- Use browser dev tools to preview and debug animations.
- Combine `transform`, `opacity`, `background`, etc., for richer effects.

---
