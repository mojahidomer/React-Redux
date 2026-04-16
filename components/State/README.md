# ⚛️ React Component State, Initial State, useState & Lazy Initialization

---

# 📌 What is State in React?

**State** is a built-in object that stores data that can change over time and affects what gets rendered.

👉 When state changes → component re-renders

```jsx
const [count, setCount] = useState(0);
```

---

# 🔥 Why State is Important?

* Makes UI **dynamic**
* Controls **user interaction**
* Helps manage **data inside components**

---

# 🧩 React Component State

## Example

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={() => setCount(count + 1)}>Increase</button>
    </div>
  );
}
```

---

# 📌 Initial State

The value passed to `useState()` is called **initial state**

```jsx
const [name, setName] = useState("Mojahid");
```

👉 `"Mojahid"` = initial state

---

## 🔹 Different Types of Initial State

### 1. Primitive

```jsx
const [count, setCount] = useState(0);
```

### 2. String

```jsx
const [name, setName] = useState("");
```

### 3. Array

```jsx
const [items, setItems] = useState([]);
```

### 4. Object

```jsx
const [user, setUser] = useState({
  name: "",
  age: 0,
});
```

---

# 🔥 Updating State

## ❌ Wrong Way (mutating)

```jsx
user.name = "John"; // ❌
```

## ✅ Correct Way

```jsx
setUser({ ...user, name: "John" });
```

---

# 🔁 Functional Update (Important)

When new state depends on old state:

```jsx
setCount(prev => prev + 1);
```

👉 Prevents stale state issues

---

# ⚡ useState Hook

`useState` is a React Hook used to add state to functional components.

```jsx
const [state, setState] = useState(initialValue);
```

* `state` → current value
* `setState` → function to update state

---

# 🔥 Lazy Initialization (Important Optimization)

Instead of:

```jsx
const [value, setValue] = useState(expensiveFunction());
```

👉 This runs on **every render** ❌

---

## ✅ Use Lazy Initialization

```jsx
const [value, setValue] = useState(() => expensiveFunction());
```

👉 Runs **only once (initial render)** ✅

---

## 🔍 Example

```jsx
function getInitialValue() {
  console.log("Expensive calculation...");
  return 100;
}

function App() {
  const [count, setCount] = useState(() => getInitialValue());

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={() => setCount(c => c + 1)}>Increase</button>
    </div>
  );
}
```

👉 `"Expensive calculation..."` runs only once

---

# 🧠 When to Use Lazy Initialization?

Use it when:

* Heavy computation
* Local storage read
* API pre-processing

---

## Example with LocalStorage

```jsx
const [theme, setTheme] = useState(() => {
  return localStorage.getItem("theme") || "light";
});
```

---

# ⚠️ Common Mistakes

## ❌ Calling function directly

```jsx
useState(getData()); // ❌
```

## ✅ Correct

```jsx
useState(() => getData()); // ✅
```

---

## ❌ Mutating state

```jsx
state.push(1); // ❌
```

## ✅ Correct

```jsx
setState([...state, 1]);
```

---

## ❌ Multiple updates issue

```jsx
setCount(count + 1);
setCount(count + 1);
```

👉 May update only once ❌

## ✅ Fix

```jsx
setCount(c => c + 1);
setCount(c => c + 1);
```

---

# 🔥 Interview Questions

---

## 1️⃣ What is state in React?

👉 State is a mutable object that controls component rendering.

---

## 2️⃣ Difference between state and props?

| State              | Props              |
| ------------------ | ------------------ |
| Mutable            | Immutable          |
| Local to component | Passed from parent |

---

## 3️⃣ What is initial state?

👉 The value passed to `useState()` during initialization.

---

## 4️⃣ What is lazy initialization?

👉 Passing a function to `useState` so it runs only once.

---

## 5️⃣ Why use functional updates?

👉 To avoid stale state issues in async updates.

---

## 6️⃣ Can we update state directly?

👉 ❌ No — must use setter function

---

## 7️⃣ When does component re-render?

👉 When state or props change

---

# 🚀 Pro Tips

* Always treat state as **immutable**
* Use functional updates for safety
* Use lazy initialization for performance
* Keep state minimal and clean

---

# 🎯 Summary

* `useState` → manage state
* Initial value → first state
* Lazy init → optimize performance
* Functional update → avoid bugs

---

💡 Master this → **you’ll clear most React interviews easily 🚀**


# 📘 HTML Forms & Input Tags – Interview Questions (Beginner → Advanced)

---

# ✅ Beginner Level

### 1. What is a `<form>` tag?

👉 The `<form>` tag is used to collect user input and send it to a server using HTTP methods like `GET` or `POST`.

---

### 2. What is `<input>` tag?

👉 `<input>` is used to take user input in different formats like text, password, email, etc.

---

### 3. What are common input types?

👉 Some common types:

* text
* password
* email
* number
* checkbox
* radio
* file
* date
* submit

---

### 4. Difference between checkbox and radio button?

| Feature   | Checkbox         | Radio                |
| --------- | ---------------- | -------------------- |
| Selection | Multiple         | Single               |
| Use case  | Multiple choices | One choice           |
| Grouping  | Independent      | Same `name` required |

---

### 5. What is `<label>` tag?

👉 It defines a label for an input and improves accessibility.

---

### 6. What is placeholder?

👉 It provides hint text inside an input field.

---

# ⚡ Intermediate Level

### 7. What is `name` attribute?

👉 It is used as a key when form data is sent to the backend.

Example:

```html id="q8x7w1"
<input name="username" />
```

---

### 8. Difference between GET and POST?

| Feature         | GET        | POST        |
| --------------- | ---------- | ----------- |
| Data visibility | URL        | Hidden      |
| Security        | Low        | Better      |
| Data size       | Limited    | Large       |
| Use case        | Fetch data | Submit data |

---

### 9. What is `required` attribute?

👉 Makes an input field mandatory before form submission.

---

### 10. Difference between `readonly` and `disabled`?

| Feature   | readonly | disabled |
| --------- | -------- | -------- |
| Editable  | ❌        | ❌        |
| Submitted | ✅        | ❌        |
| Focusable | ✅        | ❌        |

---

### 11. What is `<textarea>`?

👉 Used for multi-line text input.

---

### 12. What is `<select>` and `<option>`?

👉 Used to create dropdown lists.

---

# 🚀 Advanced Level

### 13. What is form validation?

👉 Validation ensures correct input before submission.

Types:

* HTML validation (`required`, `pattern`)
* JavaScript validation

---

### 14. What is `pattern` attribute?

👉 Used for regex validation.

```html id="t4m9y2"
<input pattern="[A-Za-z]{3}" />
```

---

### 15. What is `autocomplete`?

👉 Helps browser suggest previously entered values.

---

### 16. What is accessibility in forms?

👉 Making forms usable for all users (including screen readers).

Best practices:

* Use `<label>`
* Use `aria-*` attributes
* Proper tab navigation

---

### 17. What are controlled vs uncontrolled inputs (React)?

👉 Controlled:

* Managed by React state

👉 Uncontrolled:

* Managed by DOM

---

### 18. What is `FormData` API?

👉 Used in JavaScript to collect form data easily.

```javascript id="l1z2v3"
const formData = new FormData(form);
```

---

### 19. How to handle file uploads in forms?

👉 Use:

```html id="n8k2r5"
<input type="file" />
```

And set:

```html id="q3w9e8"
<form enctype="multipart/form-data">
```

---

### 20. What is `enctype`?

👉 Defines how form data is encoded:

* `application/x-www-form-urlencoded` (default)
* `multipart/form-data` (for files)

---

# 🔥 Expert / Real-World Level

---

### 21. How to prevent default form submission?

```javascript id="x7p2m9"
event.preventDefault();
```

---

### 22. How to handle form state in React?

👉 Using:

* `useState`
* `react-hook-form` (best practice)

---

### 23. How to improve form UX?

👉

* Inline validation
* Error messages
* Autofocus
* Proper labels

---

### 24. What are common form security issues?

👉

* XSS (Cross-Site Scripting)
* CSRF (Cross-Site Request Forgery)

---

### 25. How to make forms responsive?

👉

* Use CSS Flexbox/Grid
* Use media queries
* Avoid fixed widths

---

# 🧠 Pro Tip (Interview Answer)

If asked:

👉 *“How do you design forms in real apps?”*

Answer:

> I use semantic HTML for structure, apply validation using HTML and JavaScript, manage state using libraries like react-hook-form, and ensure accessibility and responsiveness for better user experience.

---

# 📌 Summary

* `<form>` → Container
* `<input>` → User input
* `<label>` → Accessibility
* Validation → Required for UX
* React → Controlled inputs

---

🚀 You are now fully prepared for **Forms Interview (Beginner → Advanced)**!
