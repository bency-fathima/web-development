# Understanding Indentation and Nesting in HTML Code

## 📌 What is Indentation in HTML?
Indentation refers to the **proper spacing of code** to improve readability and maintainability. In HTML, indentation is achieved by using spaces or tabs to visually separate nested elements.

### **Example of Proper Indentation**
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Properly Indented HTML</title>
    </head>
    <body>
        <header>
            <h1>Welcome to My Website</h1>
        </header>
        <main>
            <section>
                <h2>About Us</h2>
                <p>This is an example of well-indented HTML.</p>
            </section>
        </main>
        <footer>
            <p>© 2025 My Website</p>
        </footer>
    </body>
</html>
```

✅ **Why Indentation Matters?**
- **Enhances readability** – Makes it easier to understand the document structure.
- **Improves debugging** – Helps locate errors quickly.
- **Promotes best practices** – Follows clean coding conventions.

---

## 📌 What is Nesting in HTML?
Nesting refers to **placing elements inside other elements** to create a hierarchical structure. Parent elements contain child elements.

### **Example of Nested Elements**
```html
<nav>
    <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Services</a></li>
        <li><a href="#">Contact</a></li>
    </ul>
</nav>
```

✅ **Best Practices for Nesting HTML Elements:**
1. **Keep a consistent structure** – Child elements should be properly enclosed within parent elements.
2. **Avoid excessive nesting** – Too many nested elements can make the code hard to manage.
3. **Use semantic elements** – Prefer `<nav>`, `<section>`, `<article>`, and `<aside>` for better accessibility.

---

## 📌 Incorrect vs. Correct Indentation & Nesting

🚫 **Incorrect Example:**
```html
<html>
<head>
<title>Bad Indentation</title>
</head>
<body>
<h1>Title</h1>
<p>Some text</p>
<ul>
<li>Item 1<li>
<li>Item 2<li>
</ul>
</body>
</html>
```

✅ **Correct Example:**
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Good Indentation</title>
    </head>
    <body>
        <h1>Title</h1>
        <p>Some text</p>
        <ul>
            <li>Item 1</li>
            <li>Item 2</li>
        </ul>
    </body>
</html>
```

🚀 **Conclusion**
- **Indentation** ensures that your HTML is easy to read and maintain.
- **Nesting** helps in structuring web pages logically.
- Always follow **best practices** to write clean and efficient HTML!

