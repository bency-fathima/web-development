📁 flexbox-guide.md
md
Copy
Edit
# 🌐 CSS Flexbox Guide

Flexbox is a CSS layout module designed to help align and distribute space among items in a container, even when their size is unknown or dynamic.

---

## 🔹 1. Display Flex

```css
.container {
  display: flex;
}
🔹 2. Direction
css
Copy
Edit
.container {
  flex-direction: row;       /* default */
  flex-direction: row-reverse;
  flex-direction: column;
  flex-direction: column-reverse;
}
🔹 3. Wrapping
css
Copy
Edit
.container {
  flex-wrap: nowrap;         /* default */
  flex-wrap: wrap;
  flex-wrap: wrap-reverse;
}
🔹 4. Justify Content
Aligns items on the main axis (horizontal by default).

css
Copy
Edit
.container {
  justify-content: flex-start;     /* default */
  justify-content: flex-end;
  justify-content: center;
  justify-content: space-between;
  justify-content: space-around;
  justify-content: space-evenly;
}
🔹 5. Align Items
Aligns items on the cross axis (vertical by default).

css
Copy
Edit
.container {
  align-items: stretch;      /* default */
  align-items: flex-start;
  align-items: flex-end;
  align-items: center;
  align-items: baseline;
}
🔹 6. Align Self (Individual Item)
css
Copy
Edit
.item {
  align-self: auto;          /* default */
  align-self: flex-start;
  align-self: flex-end;
  align-self: center;
  align-self: baseline;
  align-self: stretch;
}
🔹 7. Gap Between Items
css
Copy
Edit
.container {
  display: flex;
  gap: 20px;
}
🔹 8. Flex Grow, Shrink, and Basis
css
Copy
Edit
.item {
  flex-grow: 1;
  flex-shrink: 1;
  flex-basis: 100px;
}
Or shorthand:

css
Copy
Edit
.item {
  flex: 1 1 100px;
}
✅ Example HTML Structure
html
Copy
Edit
<div class="container">
  <div class="item">One</div>
  <div class="item">Two</div>
  <div class="item">Three</div>
</div>
🎉 Use Case
Flexbox is ideal for:

Centering elements

Responsive layouts

Navigation bars

Cards and grids

vbnet
Copy
Edit
