📘 CSS Combinators
In CSS, combinators define the relationship between selectors. There are four main types:

1. Descendant Combinator (space)
Selects elements that are descendants (children, grandchildren, etc.) of a specific element.

css
Copy
Edit
div p {
  color: blue;
}
➡️ All <p> elements inside <div> will be blue.

2. Child Combinator (>)
Selects elements that are direct children of a specified element.

css
Copy
Edit
ul > li {
  list-style: square;
}
➡️ Only <li> elements that are direct children of <ul> will have square bullets.

3. Adjacent Sibling Combinator (+)
Selects an element that is the next sibling (immediately after) of another element.

css
Copy
Edit
h1 + p {
  font-weight: bold;
}
➡️ The first <p> immediately after an <h1> will be bold.

4. General Sibling Combinator (~)
Selects all siblings that follow a specified element.

css
Copy
Edit
h1 ~ p {
  color: green;
}
➡️ All <p> elements that come after an <h1> (not necessarily immediately) will be green.

📌 Summary Table
Combinator	Symbol	Description
Descendant	(space)	Selects all nested elements
Child	>	Selects direct children only
Adjacent	+	Selects the next immediate sibling
General	~	Selects all following siblings
