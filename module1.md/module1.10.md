# HTML Forms and Tables

## HTML Forms

HTML forms are used to collect user input. The `<form>` element wraps input elements and controls for user interaction.

### Basic Form Structure
```html
<form action="/submit" method="POST">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name" required>
    
    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>
    
    <label for="message">Message:</label>
    <textarea id="message" name="message"></textarea>
    
    <button type="submit">Submit</button>
</form>
```

### Common Form Elements

- `<input>`: Used for text fields, passwords, emails, numbers, etc.
- `<textarea>`: Multi-line input field.
- `<select>`: Dropdown selection menu.
- `<button>`: Used to submit the form.

### Example with More Input Types
```html
<form action="/register" method="POST">
    <label for="username">Username:</label>
    <input type="text" id="username" name="username" required>

    <label for="password">Password:</label>
    <input type="password" id="password" name="password" required>

    <label for="gender">Gender:</label>
    <select id="gender" name="gender">
        <option value="male">Male</option>
        <option value="female">Female</option>
    </select>

    <label>
        <input type="checkbox" name="agree" required>
        I agree to the terms and conditions
    </label>

    <button type="submit">Register</button>
</form>
```

## HTML Tables

Tables are used to display tabular data in rows and columns.

### Basic Table Structure
```html
<table border="1">
    <tr>
        <th>Name</th>
        <th>Age</th>
        <th>Country</th>
    </tr>
    <tr>
        <td>Alice</td>
        <td>25</td>
        <td>USA</td>
    </tr>
    <tr>
        <td>Bob</td>
        <td>30</td>
        <td>Canada</td>
    </tr>
</table>
```

### Table Elements
- `<table>`: Defines a table.
- `<tr>`: Table row.
- `<th>`: Table header cell (bold and centered by default).
- `<td>`: Table data cell.

### Table with `colspan` and `rowspan`
```html
<table border="1">
    <tr>
        <th colspan="2">Full Name</th>
        <th>Age</th>
    </tr>
    <tr>
        <td>John</td>
        <td>Doe</td>
        <td>28</td>
    </tr>
    <tr>
        <td rowspan="2">Jane</td>
        <td>Smith</td>
        <td>24</td>
    </tr>
    <tr>
        <td>Brown</td>
        <td>22</td>
    </tr>
</table>
```

### Styling Tables with CSS
```html
<style>
table {
    width: 100%;
    border-collapse: collapse;
}
th, td {
    border: 1px solid black;
    padding: 10px;
    text-align: left;
}
th {
    background-color: #f2f2f2;
}
</style>
```

## Summary
- Forms collect user input through various fields.
- Tables organize and present data in a structured manner.
- Proper use of attributes like `colspan` and `rowspan` enhances table presentation.
- Styling improves readability and usability.

This guide provides fundamental knowledge for working with HTML forms and tables!
