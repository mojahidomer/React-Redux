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
