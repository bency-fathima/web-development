# Data Types  

Understanding data types is crucial in programming, as they define the nature of data that can be processed. Below is an in-depth explanation of common data types:

## 1. String
A **string** is a sequence of characters, used to represent textual data.

- **Syntax**: Enclosed in quotes ('', "", or backticks in some languages).
- **Examples**: `'Hello'`, "123", `"Hello, World!"`
- **Common operations**:
  - Concatenation: `'Hello' + ' World'`
  - Length: `'Hello'.length`
  - Access: `'Hello'[0]` returns `'H'`
  - Methods: `toUpperCase()`, `toLowerCase()`, `includes()`, `slice()`

## 2. Number
A **number** can represent integers or floating-point values.

- **Syntax**: Numbers without quotes. Can be positive, negative, or decimal.
- **Examples**: `42`, `3.14`, `-100`
- **Common operations**:
  - Arithmetic: `+`, `-`, `*`, `/`, `%`
  - Conversion: `parseInt()`, `parseFloat()`
  - Methods: `toFixed()`, `toPrecision()`

## 3. Boolean
A **boolean** has only two values: `true` or `false`.

- **Used in**: Conditional statements, logic operations
- **Examples**: `true`, `false`
- **Operators**:
  - Logical: `&&`, `||`, `!`
  - Comparison: `==`, `===`, `!=`, `!==`, `<`, `>`, `<=`, `>=`

## 4. Date
Represents date and time values.

- **Syntax**: Usually created using the `Date` constructor.
- **Examples**:
  - `new Date()` - current date and time
  - `new Date("2025-01-01")`
- **Methods**:
  - `getFullYear()`, `getMonth()`, `getDate()`
  - `getHours()`, `getMinutes()`, `getSeconds()`
  - `toISOString()`, `toDateString()`

## 5. Array
An **array** is an ordered collection of values.

- **Syntax**: Enclosed in square brackets `[]`
- **Examples**: `[1, 2, 3]`, `['a', 'b', 'c']`, `[true, 42, 'hello']`
- **Features**:
  - Index-based access
  - Can hold mixed data types
- **Methods**:
  - `push()`, `pop()`, `shift()`, `unshift()`
  - `map()`, `filter()`, `reduce()`, `forEach()`

## 6. Object
An **object** is a collection of key-value pairs.

- **Syntax**: Enclosed in curly braces `{}`
- **Examples**:
  ```js
  const person = {
    name: 'Alice',
    age: 30,
    isStudent: false
  };
  ```
- **Features**:
  - Keys are strings (or Symbols)
  - Values can be any data type
- **Access**:
  - Dot notation: `person.name`
  - Bracket notation: `person['age']`

## 7. ObjectId
**ObjectId** is a special type used primarily in MongoDB to uniquely identify documents.

- **Structure**: A 12-byte identifier typically represented as a 24-character hexadecimal string.
- **Example**: `ObjectId("507f191e810c19729de860ea")`
- **Components**:
  - 4-byte timestamp
  - 5-byte random value
  - 3-byte incrementing counter
- **Usage**: Primary keys in MongoDB documents

## 8. Null
**Null** is a special value representing "no value" or "empty".

- **Syntax**: `null`
- **Usage**: Used to intentionally indicate the absence of any object value
- **Difference from undefined**:
  - `null` is explicitly assigned
  - `undefined` is the default value for uninitialized variables

---

These data types form the foundation for building applications, manipulating data, and storing structured information. Understanding their behavior is essential for effective programming.

