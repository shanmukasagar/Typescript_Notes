# 📘 TypeScript Notes

Welcome to my TypeScript learning notes — a beginner-friendly, clean guide to mastering TypeScript with simple examples and best practices.

---

## 📌 What is TypeScript?

- TypeScript is a **superset of JavaScript** developed by Microsoft.
- It adds **static typing** to JavaScript.
- TypeScript code compiles into plain JavaScript.
- Files use the `.ts` extension.

---

## 🎯 Why Learn TypeScript (Even If You Know JavaScript)

✅ **Catch Errors Early** — Avoid bugs before you run the code  
✅ **Better Developer Experience** — Autocomplete, IntelliSense, tool support  
✅ **Improved Readability** — Clear input/output structure  
✅ **Safer Refactoring** — Type-aware code changes  
✅ **Great for Large Projects** — Maintains structure and reduces bugs

---

## 🔁 JavaScript vs TypeScript Example

### JavaScript (No Type Checking)
```js
function greet(name) {
  return "Hello " + name.toUpperCase();
}

console.log(greet(123)); // ❌ Runtime Error
```

### TypeScript (With Type Checking)
```ts
function greet(name: string): string {
  return "Hello " + name.toUpperCase();
}

console.log(greet(123)); // ❌ Compile-time Error
```

---

## ⚙️ Getting Started with TypeScript

### ✅ 1. Install TypeScript
```bash
npm install -g typescript
tsc --version
```

### ✅ 2. Initialize Project
```bash
mkdir my-ts-project
cd my-ts-project
npm init -y
tsc --init
```

### ✅ 3. Create and Compile File
```bash
echo "let msg: string = 'Hello TypeScript'; console.log(msg);" > index.ts
tsc index.ts
node index.js
```

---

## 🔡 Basic Types in TypeScript

### 🔹 Number
```ts
let age: number = 25;
let pi: number = 3.14;
```

### 🔹 String
```ts
let name: string = "Shanmukasagar";
let greeting: string = `Hello, ${name}`;
```

### 🔹 Boolean
```ts
let isLoggedIn: boolean = true;
```

---

## 🧩 Custom Types

### 🔸 `type` (Type Alias)
```ts
type Gender = "male" | "female" | "other";
let userGender: Gender = "male";
```

### 🔸 `interface` (Object Shape)
```ts
interface User {
  name: string;
  age: number;
  isAdmin: boolean;
}

const user: User = { name: "Sagar", age: 25, isAdmin: false };
```

---

## ⚠️ The `any` Type

### ❌ Avoid This:
```ts
let data: any = "hello";
data = 123; // ✅ But unsafe
```

### ✅ Prefer `unknown` Instead
```ts
let value: unknown = "hello";
if (typeof value === "string") {
  console.log(value.toUpperCase());
}
```

---

## 🧠 Functions in TypeScript

### 🔹 Basic Function
```ts
function add(a: number, b: number): number {
  return a + b;
}
```

### 🔹 Arrow Function
```ts
const greet = (user: string): string => `Hello ${user.toUpperCase()}`;
```

### 🔹 Function with Interface
```ts
interface User {
  name: string;
  age: number;
}

const printUser = (user: User): string => {
  return `${user.name} is ${user.age} years old.`;
};
```

---

## 🧳 Returning Arrays and Objects

### 🔹 Array Return
```ts
function getFruits(): string[] {
  return ["apple", "banana"];
}
```

### 🔹 Object Return
```ts
type User = { name: string; age: number };

function getUser(): User {
  return { name: "Sagar", age: 25 };
}
```

### 🔹 Array of Objects
```ts
type Product = { name: string; price: number };

function getProducts(): Product[] {
  return [
    { name: "Laptop", price: 50000 },
    { name: "Phone", price: 25000 }
  ];
}
```

---

## 🚨 Common Mistakes with Objects

| Problem                         | Fix                                  |
|-------------------------------|--------------------------------------|
| Accessing missing props       | Use interfaces/types                 |
| Accidental mutation           | Use object spread (`{ ...obj }`)     |
| Using `any` type              | Use proper types/interfaces          |
| Duplicate object keys         | Avoid duplicate property names       |
| Deep nested object crashes    | Use optional chaining (`?.`)         |

---

## 🆚 `interface` vs `type`

| Feature                  | `interface`     | `type`              |
|--------------------------|----------------|---------------------|
| Extending                | ✅ `extends`    | ✅ `&` (intersection)|
| Works with primitives    | ❌              | ✅                  |
| Declaration merging      | ✅              | ❌                  |
| Supports union types     | ❌              | ✅                  |

### 🔸 Example – Extending Types
```ts
interface Person {
  name: string;
}
interface Employee extends Person {
  salary: number;
}

type PersonType = { name: string };
type EmployeeType = PersonType & { salary: number };
```

---

## 🏷️ Type Alias Use Cases

```ts
// Primitive alias
type Username = string;

// Object alias
type User = { name: string; age: number };

// Union types
type Status = "loading" | "success" | "error";

// Array of objects
type ProductList = Product[];

// Function type
type GreetFunction = (name: string) => string;
```

---

## ✅ Best Practices

- ✅ Always define **parameter and return types** in functions
- ✅ Use `interface` or `type` for complex data
- ✅ Avoid using `any`
- ✅ Prefer `arrow functions` for cleaner code
- ✅ Use `optional chaining (?.)` to prevent deep object crashes
- ✅ Use `unknown` instead of `any` for safer dynamic values

---

## 🚀 Coming Up Next

- Enums
- Tuples
- Generics
- Type Guards
- Classes
- React with TypeScript
- Real-world Projects

---

## 👨‍💻 Author

**Shanmukasagar**  
Full-stack MERN Developer | Passionate about TypeScript & clean code  
📫 [LinkedIn](https://www.linkedin.com) *(Add your profile link)*

---
