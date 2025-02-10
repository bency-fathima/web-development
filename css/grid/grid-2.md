# Understanding CSS Grid

## What Happens When `display: grid;` is Set?

When an element's `display` property is set to `grid`, it becomes a **grid container**, and its direct children become **grid items**. The grid layout allows for precise positioning of items in rows and columns, making it a powerful tool for designing web page structures.

## Basic Example of CSS Grid

### HTML Structure
```html
<div class="container">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
  <div class="item">4</div>
  <div class="item">5</div>
  <div class="item">6</div>
</div>
```

### CSS Styling
```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
}

.item {
  background-color: lightblue;
  padding: 20px;
  text-align: center;
}
```

## Explanation
- **`display: grid;`** – Turns `.container` into a grid container.
- **`grid-template-columns: repeat(3, 1fr);`** – Defines a three-column layout where each column takes up an equal fraction (`1fr`) of the available space.
- **`gap: 10px;`** – Adds spacing between the grid items.
- Each `.item` is automatically placed inside the defined grid structure.

## Result
This setup will create a layout where six items are arranged in a **3-column grid**, distributing them evenly while maintaining spacing between elements.

## When to Use CSS Grid
- When a **two-dimensional** layout (rows & columns) is needed.
- When **precise placement** of elements is required.
- When designing **responsive layouts** efficiently.

## Conclusion
CSS Grid provides a flexible and powerful way to create structured layouts. By understanding how `display: grid;` works, developers can efficiently organize content without relying heavily on floats or flexbox.
