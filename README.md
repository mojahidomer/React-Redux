# 🚀 JSX Embedding & Tricky Interview Questions (React)

## 📌 What is JSX?

JSX (JavaScript XML) allows you to write HTML-like syntax inside JavaScript.

```jsx
const element = <h1>Hello World</h1>;
```

---

# 🔥 JSX Embedding

JSX allows embedding JavaScript using `{}`

---

## ✅ 1. JSX Expression

You can use any **valid JavaScript expression** inside `{}`

```jsx
const name = "Mojahid";

<h1>Hello {name}</h1>
<h1>{10 + 20}</h1>
```

### ❌ Not Allowed (Statements)

```jsx
if (true) {}   // ❌
for (...) {}   // ❌
```

### ✅ Use Instead

```jsx
{condition && <p>Show</p>}
{condition ? <A /> : <B />}
```

---

## ✅ 2. JSX Attributes

```jsx
const url = "https://google.com";

<a href={url}>Visit</a>
<button disabled={true}>Click</button>
```

### Inline Style

```jsx
<div style={{ color: "red", fontSize: "20px" }}>
  Styled Text
</div>
```

---

## ✅ 3. JSX Children

```jsx
<div>Hello World</div>
```

### Dynamic Children

```jsx
const user = "Mojahid";
<div>{user}</div>
```

### Passing Children

```jsx
function Card({ children }) {
  return <div>{children}</div>;
}

<Card>
  <h1>Inside Card</h1>
</Card>
```

---

# 🔥 Tricky JSX Interview Questions

---

## 1️⃣ Logical AND

```jsx
const name = "Mojahid";
<h1>{name && "Hello"}</h1>
```

✅ Output: `Hello`

---

## 2️⃣ Empty String

```jsx
const name = "";
<h1>{name && "Hello"}</h1>
```

✅ Output: nothing

---

## 3️⃣ Zero Edge Case

```jsx
<h1>{0 && "Hello"}</h1>
```

✅ Output: `0`

⚠️ React renders `0`

---

## 4️⃣ Fix Bug

```jsx
{items.length && <List />}
```

❌ Problem: renders `0`

✅ Fix:

```jsx
{items.length > 0 && <List />}
```

---

## 5️⃣ Ignored Values

```jsx
<h1>{true}</h1>
<h1>{false}</h1>
<h1>{null}</h1>
<h1>{undefined}</h1>
```

✅ Output: nothing

---

## 6️⃣ Array Rendering

```jsx
<h1>{[1, 2, 3]}</h1>
```

✅ Output: `123`

---

## 7️⃣ Object Error

```jsx
<h1>{{ name: "Mojahid" }}</h1>
```

❌ Error: Objects are not valid as React child

✅ Fix:

```jsx
<h1>{JSON.stringify({ name: "Mojahid" })}</h1>
```

---

## 8️⃣ Ternary Operator

```jsx
const isLoggedIn = false;
<h1>{isLoggedIn ? "Welcome" : "Login"}</h1>
```

✅ Output: `Login`

---

## 9️⃣ String vs Number

```jsx
const value = "0";
<h1>{value && "Hello"}</h1>
```

✅ Output: `Hello`

---

## 🔟 List Rendering Issue

```jsx
{items.map(item => <li>{item}</li>)}
```

❌ Missing key

✅ Fix:

```jsx
{items.map((item, index) => (
  <li key={index}>{item}</li>
))}
```

---

## 1️⃣1️⃣ Function Execution Bug

```jsx
<button onClick={handleClick()}>
```

❌ Executes immediately

✅ Fix:

```jsx
<button onClick={handleClick}>
<button onClick={() => handleClick()}>
```

---

## 1️⃣2️⃣ Optional Chaining

```jsx
const user = null;
<h1>{user?.name}</h1>
```

✅ Output: nothing (no crash)

---

## 1️⃣3️⃣ class vs className

```jsx
<div class="box">Hello</div>
```

❌ Wrong

✅ Fix:

```jsx
<div className="box">Hello</div>
```

---

## 1️⃣4️⃣ Multiple Conditions

```jsx
const count = 5;
<h1>{count > 3 && count < 10 && "Valid"}</h1>
```

✅ Output: `Valid`

---

## 1️⃣5️⃣ Nested Conditions

```jsx
const role = "admin";

<h1>
  {role === "admin"
    ? "Admin"
    : role === "user"
    ? "User"
    : "Guest"}
</h1>
```

✅ Output: `Admin`

---

# 🧠 Important Interview Notes

* JSX supports **expressions, not statements**
* `&&` returns:

  * first falsy OR last truthy value
* `0` is rendered ⚠️
* `false`, `null`, `undefined` are ignored
* Arrays ✅ render
* Objects ❌ do not render
* Always use `key` in lists
* `children` is just a prop

---

# 🔥 Pro Tips

* Prefer ternary for complex conditions
* Avoid nested ternary (readability issue)
* Use optional chaining to prevent crashes
* Keep JSX clean and readable

---

# 🚀 Practice Questions

1. What will `{false && "Hello"}` render?
2. Why does `{0 && <Comp />}` render `0`?
3. Difference between `{}` and `""` in JSX?
4. Why objects cannot be rendered?
5. When to use `&&` vs ternary?

---

# 🎯 Summary

JSX is:

* Declarative
* Powerful
* Expression-based

Mastering JSX = clearing **React interviews easily 🚀**

---
