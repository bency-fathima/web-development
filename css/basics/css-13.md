📄 css-variables.md
md
Copy
Edit
# CSS Variables (Custom Properties)

CSS Variables, or Custom Properties, allow you to store values in reusable variables throughout your CSS. They make styling more consistent and easier to maintain.

---

## ✅ Syntax

```css
:root {
  --primary-color: #3498db;
  --font-size-large: 1.5rem;
}
Variables are defined inside a selector using -- prefix.

:root is commonly used to define global variables (acts like a global scope).

🎯 Usage
css
Copy
Edit
body {
  color: var(--primary-color);
  font-size: var(--font-size-large);
}
var(--variable-name) is used to apply the value of a CSS variable.

🔁 Fallback Values
css
Copy
Edit
p {
  color: var(--undefined-color, black);
}
If --undefined-color is not defined, it will fallback to black.

🧠 Advantages
💡 Reusability

🛠️ Easier to maintain themes

🌓 Supports dynamic theming (light/dark mode)

♻️ Reduces repetition

🎨 Example: Theme Switcher
css
Copy
Edit
:root {
  --bg-color: white;
  --text-color: black;
}

[data-theme="dark"] {
  --bg-color: black;
  --text-color: white;
}

body {
  background-color: var(--bg-color);
  color: var(--text-color);
}
You can dynamically switch the theme by toggling the data-theme attribute in HTML.

❗Notes
CSS Variables can be overridden in lower scopes.

They are not supported in IE 11 or below.

Variables work only in the properties that accept values.

