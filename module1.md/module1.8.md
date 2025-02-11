# How to Create Multi-Page Websites Using HTML

## 📌 Introduction to Multi-Page Websites

A **multi-page website** consists of multiple HTML files linked together using **anchor (`<a>`) tags** for navigation.

---

## 📌 Basic Folder Structure for a Multi-Page Website

```
/my-website
│── index.html        (Home Page)
│── about.html        (About Page)
│── contact.html      (Contact Page)
│── styles.css        (CSS File)
│── images/           (Folder for Images)
└── js/               (Folder for JavaScript)
```

### **Example: Navigation Bar Across Pages**
```html
<nav>
    <ul>
        <li><a href="index.html">Home</a></li>
        <li><a href="about.html">About</a></li>
        <li><a href="contact.html">Contact</a></li>
    </ul>
</nav>
```

---

## 📌 Creating the Home Page (`index.html`)
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Home</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <nav>
        <a href="index.html">Home</a> | 
        <a href="about.html">About</a> | 
        <a href="contact.html">Contact</a>
    </nav>
    <h1>Welcome to My Website</h1>
    <p>This is the home page of our multi-page website.</p>
</body>
</html>
```

---

## 📌 Creating the About Page (`about.html`)
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <nav>
        <a href="index.html">Home</a> | 
        <a href="about.html">About</a> | 
        <a href="contact.html">Contact</a>
    </nav>
    <h1>About Us</h1>
    <p>We are a company that builds multi-page websites.</p>
</body>
</html>
```

---

## 📌 Creating the Contact Page (`contact.html`)
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contact</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <nav>
        <a href="index.html">Home</a> | 
        <a href="about.html">About</a> | 
        <a href="contact.html">Contact</a>
    </nav>
    <h1>Contact Us</h1>
    <p>Email: contact@example.com</p>
</body>
</html>
```

---

## 📌 Adding a Common CSS File (`styles.css`)
```css
body {
    font-family: Arial, sans-serif;
    text-align: center;
}

nav a {
    text-decoration: none;
    margin: 10px;
    font-size: 18px;
}

h1 {
    color: blue;
}
```

---

## 📌 How It Works
1. The **navigation bar** links all pages together.
2. Clicking a link **loads a new HTML page** (without reloading the entire website).
3. The **CSS file (`styles.css`)** keeps styles consistent across all pages.

🚀 **Now you can create a multi-page website using HTML!**

