# CSS Tables

CSS provides various properties to style tables, making them more visually appealing and easier to read.

---

## 1. Basic Table Styling
The default table styling can be modified using basic properties.
```css
table {
    width: 100%;
    border-collapse: collapse;
}
th, td {
    border: 1px solid black;
    padding: 10px;
    text-align: left;
}
```

### Explanation:
- `width: 100%`: Makes the table occupy full width.
- `border-collapse: collapse`: Merges cell borders into a single border.
- `border: 1px solid black`: Adds a border to table cells.
- `padding: 10px`: Adds space inside each cell.
- `text-align: left`: Aligns text to the left.

---

## 2. Adding Table Borders
Defines the border style for table elements.
```css
table, th, td {
    border: 2px solid blue;
    border-collapse: collapse;
}
```

---

## 3. Table Header Styling
You can style the table header differently for better readability.
```css
th {
    background-color: #f4f4f4;
    color: black;
    font-weight: bold;
}
```

---

## 4. Alternating Row Colors
Creates a striped effect for better visibility.
```css
tr:nth-child(even) {
    background-color: #f2f2f2;
}
```

---

## 5. Hover Effect on Rows
Enhances user interaction with hover effects.
```css
tr:hover {
    background-color: #ddd;
}
```

---

## 6. Centering Table Content
Aligns text and centers the table.
```css
table {
    margin: auto;
    text-align: center;
}
```

---

## 7. Fixed Table Layout
Controls how table cells resize when content overflows.
```css
table {
    table-layout: fixed;
}
```

---

## 8. Example: Styled Table

### HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Table Example</title>
    <style>
        table {
            width: 80%;
            border-collapse: collapse;
            margin: auto;
        }
        th, td {
            border: 1px solid black;
            padding: 10px;
            text-align: center;
        }
        th {
            background-color: #f4f4f4;
        }
        tr:nth-child(even) {
            background-color: #f2f2f2;
        }
        tr:hover {
            background-color: #ddd;
        }
    </style>
</head>
<body>
    <table>
        <tr>
            <th>Name</th>
            <th>Age</th>
            <th>Country</th>
        </tr>
        <tr>
            <td>John Doe</td>
            <td>30</td>
            <td>USA</td>
        </tr>
        <tr>
            <td>Jane Smith</td>
            <td>25</td>
            <td>Canada</td>
        </tr>
        <tr>
            <td>Mark Brown</td>
            <td>35</td>
            <td>UK</td>
        </tr>
    </table>
</body>
</html>
```

### Explanation:
- The table has borders, padding, and background colors for better readability.
- The `nth-child(even)` property adds alternating row colors.
- The `tr:hover` effect highlights a row when hovered.

---

## Conclusion
CSS allows you to customize tables to enhance their appearance and usability. Proper styling ensures tables are readable, accessible, and visually appealing.
