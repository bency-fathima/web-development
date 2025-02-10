# Positioning Items in a CSS Grid

## Introduction
CSS Grid allows precise positioning of items within a grid by specifying their placement across rows and columns. This guide explains how to position items effectively and provides examples of grid placement.

## Basic Grid Positioning
To position items in a grid, use the `grid-column` and `grid-row` properties.

### 1. Define a Grid Container
```css
.container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(3, 100px);
  gap: 10px;
}
```

### 2. Add Grid Items
```html
<div class="container">
  <div class="item item1">1</div>
  <div class="item item2">2</div>
  <div class="item item3">3</div>
  <div class="item item4">4</div>
  <div class="item item5">5</div>
</div>
```

### 3. Position Items Explicitly
```css
.item1 {
  grid-column: 1 / 3; /* Spans from column 1 to 3 */
  grid-row: 1 / 2; /* Placed in row 1 */
}

.item2 {
  grid-column: 3 / 5; /* Spans from column 3 to 5 */
  grid-row: 1 / 3; /* Spans two rows */
}

.item3 {
  grid-column: 1 / 2; /* Placed in column 1 */
  grid-row: 2 / 4; /* Spans from row 2 to 4 */
}

.item4 {
  grid-column: 2 / 4; /* Spans two columns */
  grid-row: 3 / 4; /* Placed in row 3 */
}

.item5 {
  grid-column: 4 / 5; /* Placed in column 4 */
  grid-row: 2 / 3; /* Placed in row 2 */
}
```

## Explanation
- **`grid-column: start / end;`** defines the start and end column position of an item.
- **`grid-row: start / end;`** defines the start and end row position of an item.
- Items can **span multiple rows or columns** by specifying a range.
- Grid items **automatically adjust** based on defined grid structure.

## Conclusion
CSS Grid provides powerful tools for **precisely positioning elements** across rows and columns. Using `grid-column` and `grid-row`, elements can be arranged flexibly, allowing for complex layouts with ease.

