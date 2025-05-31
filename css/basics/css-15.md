
# CSS Shadows

CSS provides two main ways to add shadows to elements:

---

## 1. Text Shadow

Used to apply shadow effects to **text**..

```css
selector {
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
}
```

### Syntax Breakdown:
- `2px`: Horizontal shadow (to the right)
- `2px`: Vertical shadow (downward)
- `4px`: Blur radius
- `rgba(...)`: Color of the shadow (supports transparency)

### Example:

```css
h1 {
  text-shadow: 1px 1px 2px #888;
}
```

---

## 2. Box Shadow

Used to apply shadows to **box-like elements** (e.g., `div`, `button`, `card`, etc.)

```css
selector {
  box-shadow: 4px 4px 10px rgba(0, 0, 0, 0.3);
}
```

### Syntax Breakdown:
- `4px`: Horizontal offset
- `4px`: Vertical offset
- `10px`: Blur radius
- `rgba(...)`: Shadow color

### Example:

```css
.card {
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}
```

---

## Optional Parameters

You can also add:
- **Spread radius**
- **Inset** keyword for inner shadows

### Examples:

```css
/* Spread radius added */
box-shadow: 0 4px 8px 2px rgba(0, 0, 0, 0.2);

/* Inset shadow (inside the box) */
box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.2);
```
---

## Notes

- You can use multiple shadows separated by commas.
- Shadows enhance UI by adding depth and realism.
