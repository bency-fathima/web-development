# Combining CSS Grid and Flexbox for Complex Layouts

## Introduction
CSS Grid and Flexbox can be used together to create **powerful and flexible layouts**. Grid is best suited for **overall page structure**, while Flexbox is ideal for **arranging items within grid cells**.

## Setting Up a Grid with Flexbox Items

### 1. Define the Grid Container
```css
.container {
  display: grid;
  grid-template-columns: 1fr 2fr;
  grid-template-rows: auto auto;
  gap: 20px;
}
```

### 2. Add Grid Items with Flexbox Inside
```html
<div class="container">
  <header class="header">Header</header>
  <nav class="sidebar">Sidebar</nav>
  <main class="content">
    <div class="cards">
      <div class="card">Item 1</div>
      <div class="card">Item 2</div>
      <div class="card">Item 3</div>
    </div>
  </main>
</div>
```

### 3. Apply Flexbox to Grid Items
```css
.header {
  grid-column: 1 / 3;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #4CAF50;
  padding: 20px;
  color: white;
}

.sidebar {
  grid-column: 1 / 2;
  grid-row: 2 / 3;
  background: #2196F3;
  padding: 20px;
  color: white;
}

.content {
  grid-column: 2 / 3;
  grid-row: 2 / 3;
  background: #FFC107;
  padding: 20px;
}

.cards {
  display: flex;
  gap: 10px;
}

.card {
  flex: 1;
  background: white;
  padding: 20px;
  border: 1px solid #ccc;
}
```

## Explanation
- **Grid handles overall structure**, defining the main layout.
- **Flexbox is used inside the `.cards` container** to arrange items in a row with equal spacing.
- The `.header` spans both columns using `grid-column: 1 / 3`.
- The `.sidebar` and `.content` occupy separate sections within the grid.

## When to Use Grid with Flexbox
- Use **Grid** for defining large-scale layout structures (e.g., page templates, dashboards).
- Use **Flexbox** inside grid cells for handling flexible content (e.g., navigation menus, card layouts).

## Conclusion
By combining CSS Grid for layout structuring and Flexbox for arranging elements inside grid cells, you can create **responsive and scalable** web designs efficiently.
