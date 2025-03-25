# Fonts in CSS

In CSS, fonts can be customized using various properties to control the typography of your webpage. The most common font-related properties are `font-family`, `font-size`, `font-weight`, `font-style`, `line-height`, and more.

## 1. `font-family`

The `font-family` property defines the typeface of the text. You can specify multiple fonts, so the browser will use the first available font in the list.

### Example:

```css
body {
  font-family: 'Arial', sans-serif;
}
```

### Font Stacks:

- **Generic Font Families:** These are fallback options like `serif`, `sans-serif`, `monospace`.

- **Web-safe Fonts:** These are fonts that are available across most operating systems, like `Arial`, `Courier`, and `Georgia`.

- **Custom Fonts:** You can also use custom fonts by linking to external font services like Google Fonts.

## 2. `font-size`

The `font-size` property defines the size of the text. The value can be specified in various units, such as `px`, `em`, `rem`, `%`, `vw`, and `vh`.

### Example:

```css
h1 {
  font-size: 32px;
}

p {
  font-size: 1.2em;
}
```

### Units:

- **px:** Pixels, a fixed size.

- **em:** Relative to the `font-size` of the parent element.

- **rem:** Relative to the `font-size` of the root element (`<html>`).

- **%:** Relative to the `font-size` of the parent element.

## 3. `font-weight`

The `font-weight` property defines the thickness of the font. Common values are `normal`, `bold`, or numeric values ranging from `100` to `900`.

### Example:

```css
h1 {
  font-weight: bold;
}

p {
  font-weight: 300;
}
```

### Values:

- **normal (400)**

- **bold (700)**

- **bolder:** A stronger weight than the parent element.

- **lighter:** A lighter weight than the parent element.

## 4. `font-style`

The `font-style` property allows you to specify whether the text should be italicized or not. The common values are `normal`, `italic`, and `oblique`.

### Example:

```css
em {
  font-style: italic;
}

p {
  font-style: oblique;
}
```

### Values:

- **normal:** Default style, no slant.

- **italic:** The text is italicized.

- **oblique:** The text is slanted, similar to italic but not exactly the same.

