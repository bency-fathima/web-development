# How to Insert Images Using HTML

## 📌 Introduction to the `<img>` Tag

In HTML, images are inserted using the `<img>` tag. This tag is **self-closing**, meaning it does not require a closing tag.

### **Basic Syntax of the `<img>` Tag**
```html
<img src="image.jpg" alt="Description of Image">
```

✅ **Attributes of the `<img>` Tag:**
- **`src` (source)**: Specifies the image URL or file path.
- **`alt` (alternative text)**: Provides a description for accessibility and when the image cannot load.
- **`width` and `height`**: Define image dimensions in pixels or percentages.

---

## 📌 Inserting an Image from Different Sources

### **1️⃣ Adding an Image from a Local File**
```html
<img src="images/photo.jpg" alt="A beautiful scenery" width="400" height="300">
```
📌 *Ensure the image file exists in the specified folder (`images/photo.jpg`).*

### **2️⃣ Adding an Image from a URL**
```html
<img src="https://example.com/image.jpg" alt="Online Image">
```

### **3️⃣ Adding an Image from an External CDN**
```html
<img src="https://cdn.example.com/logo.png" alt="Website Logo" width="100">
```

---

## 📌 Resizing and Styling Images

### **1️⃣ Using `width` and `height` Attributes**
```html
<img src="image.jpg" width="300" height="200" alt="Resized Image">
```

### **2️⃣ Using CSS for Responsive Images**
```html
<style>
    img {
        max-width: 100%;
        height: auto;
    }
</style>
<img src="responsive.jpg" alt="Responsive Image">
```

---

## 📌 Using Images as Links

You can wrap an `<img>` tag inside an `<a>` tag to make it clickable:

```html
<a href="https://example.com">
    <img src="logo.png" alt="Click to Visit Example" width="150">
</a>
```

---

## 📌 Adding Background Images with CSS

Instead of using `<img>`, you can use CSS to set an image as a background:

```html
<style>
    .banner {
        background-image: url('background.jpg');
        width: 100%;
        height: 300px;
        background-size: cover;
    }
</style>
<div class="banner"></div>
```

---

## 📌 Conclusion

- Use the `<img>` tag to **display images** in HTML.
- Always include the **`alt` attribute** for **accessibility** and **SEO benefits**.
- Use **CSS** to make images **responsive** and style them effectively.
- Images can be **local files, external URLs, or CDN-hosted resources**.

🚀 **Now you know how to insert images in HTML!**

