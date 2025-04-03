# CSS `position` Property

The `position` property in CSS specifies how an element is positioned in a document. It plays a crucial role in determining how an element is placed in relation to its normal flow and other elements.

## Syntax

```css
position: static | relative | absolute | fixed | sticky;
1. static (default)
Elements are positioned according to the normal flow of the document.

No special positioning is applied.

css
Copy
Edit
.box {
  position: static;
}
✅ Note: top, right, bottom, and left have no effect on static elements.

2. relative
The element is positioned relative to its normal position.

You can use top, right, bottom, left to move it.

css
Copy
Edit
.box {
  position: relative;
  top: 10px;
  left: 20px;
}
📝 Note: Space is still reserved for the element in its original position.

3. absolute
The element is positioned relative to the nearest positioned ancestor (not static).

If no such ancestor exists, it is placed relative to the <html> element.

css
Copy
Edit
.box {
  position: absolute;
  top: 10px;
  left: 20px;
}
📌 Note: The element is removed from the normal document flow.

4. fixed
The element is positioned relative to the browser window (viewport).

It does not move when the page is scrolled.

css
Copy
Edit
.box {
  position: fixed;
  bottom: 0;
  right: 0;
}
🎯 Use Case: Sticky headers or floating buttons.

5. sticky
A hybrid of relative and fixed.

The element toggles between relative and fixed depending on scroll position.

css
Copy
Edit
.box {
  position: sticky;
  top: 0;
}
📌 Note: It works within the bounds of its container.

Example
html
Copy
Edit
<div class="container">
  <div class="box static">Static</div>
  <div class="box relative">Relative</div>
  <div class="box absolute">Absolute</div>
  <div class="box fixed">Fixed</div>
  <div class="box sticky">Sticky</div>
</div>
css
Copy
Edit
.container {
  position: relative;
  height: 2000px;
  padding: 50px;
}
.box {
  width: 150px;
  height: 50px;
  margin: 10px;
  color: white;
  text-align: center;
  line-height: 50px;
}
.static { background: gray; position: static; }
.relative { background: blue; position: relative; top: 20px; left: 10px; }
.absolute { background: red; position: absolute; top: 100px; left: 100px; }
.fixed { background: green; position: fixed; top: 0; right: 0; }
.sticky { background: orange; position: sticky; top: 0; }
Summary Table
Value	Description
static	Default, no positioning applied
relative	Relative to its normal position
absolute	Relative to nearest positioned ancestor or <html>
fixed	Fixed to the viewport
sticky	Scrolls with the page until a threshold is met
