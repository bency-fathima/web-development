# How to Create Hyperlinks Using Anchor Tags in HTML

## 📌 Introduction to Anchor Tags (`<a>`)

In HTML, the `<a>` (anchor) tag is used to create **hyperlinks**, allowing users to navigate between web pages or external sites.

### **Basic Syntax of an Anchor Tag**
```html
<a href="https://example.com">Visit Example</a>
```

✅ **Key Attributes of the `<a>` Tag:**
- **`href`**: Specifies the URL or path the link points to.
- **`target`**: Defines where the linked document will open (`_blank`, `_self`, `_parent`, `_top`).
- **`title`**: Provides additional information (shown as a tooltip).
- **`rel`**: Defines the relationship between the current and linked document (e.g., `nofollow`, `noopener`).

---

## 📌 Types of Hyperlinks

### **1️⃣ Linking to an External Website**
```html
<a href="https://www.google.com" target="_blank" rel="noopener noreferrer">Visit Google</a>
```
📌 *Opens the link in a **new tab** (`_blank`) for better user experience.*

### **2️⃣ Linking to Another Page in the Same Website**
```html
<a href="about.html">About Us</a>
```
📌 *Navigates to the `about.html` page within the same site.*

### **3️⃣ Linking to a Specific Section on the Same Page (Anchor Links)**
```html
<a href="#contact">Go to Contact Section</a>

<!-- Target Section -->
<h2 id="contact">Contact Us</h2>
```
📌 *Clicking the link scrolls directly to the `#contact` section.*

### **4️⃣ Creating an Email Link**
```html
<a href="mailto:info@example.com">Email Us</a>
```
📌 *Opens the user's default email application to send an email.*

### **5️⃣ Creating a Phone Call Link**
```html
<a href="tel:+1234567890">Call Us</a>
```
📌 *Clicking the link on a mobile device opens the dialer.*

---

## 📌 Styling Hyperlinks with CSS

### **1️⃣ Changing Link Colors**
```html
<style>
    a {
        color: blue;
        text-decoration: none;
    }
    a:hover {
        color: red;
        text-decoration: underline;
    }
</style>
```

### **2️⃣ Making a Button-Like Link**
```html
<a href="https://example.com" style="display: inline-block; padding: 10px 20px; background: blue; color: white; text-decoration: none; border-radius: 5px;">Click Here</a>
```

---

## 📌 Conclusion

- Use the `<a>` tag to **create hyperlinks** for navigation.
- Use `href` for the destination URL and `target="_blank"` for opening in a new tab.
- Anchor links (`#id`) help **navigate within the same page**.
- Use **CSS** to style hyperlinks for better user experience.

🚀 **Now you know how to create hyperlinks using anchor tags in HTML!**

