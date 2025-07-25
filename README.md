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

# 📘 TypeScript Notes – Part 2

## ✅ `readonly` – Makes a property non-editable

**🔹 Meaning:** You cannot change this property's value after the object is created.

```ts
interface User {
  readonly id: number;
  name: string;
}

const user: User = {
  id: 1,
  name: "Sagar"
};

user.name = "Shanmukasagar"; // ✅ Allowed
user.id = 2; // ❌ Error: Cannot assign to 'id' because it is a read-only property.
```

---

## ✅ `?` (Optional) – Makes a property not required

**🔹 Meaning:** This property may or may not exist on the object.

```ts
interface User {
  name: string;
  age?: number; // optional
}

const user1: User = { name: "Sagar" }; // ✅ age is optional
const user2: User = { name: "Sagar", age: 25 }; // ✅ also valid
```

---

## 🧩 Combine `readonly` and `optional`

```ts
interface User {
  readonly id?: number; // optional and readonly
  name: string;
}
```

---

## ✅ Array in TypeScript (Typed Arrays)

### 🔸 1. Array of Strings
```ts
let names: string[] = ["Sagar", "John"];
names.push("Alice"); // ✅
names.push(123); // ❌ Error: number not assignable to string
```

### 🔸 2. Array of Numbers
```ts
let scores: number[] = [90, 85, 75];
```

### 🔸 3. Array of Booleans
```ts
let flags: boolean[] = [true, false];
```

### 🔸 4. Array of Objects
```ts
type User = {
  name: string;
  age: number;
};

let users: User[] = [
  { name: "Sagar", age: 25 },
  { name: "John", age: 30 }
];
```

### 🔸 5. Readonly Arrays
```ts
const items: readonly string[] = ["A", "B"];
// items.push("C"); ❌ Error: Cannot modify readonly array
```

### 🔸 6. Alternative Syntax – `Array<Type>`
```ts
let prices: Array<number> = [10, 20, 30];
// Same as number[]
```

---

## ✅ What is a Union Type?

A Union Type allows a variable to have more than one type.

```ts
type Variable = type1 | type2 | type3;
```

### 🔸 1. Basic Example
```ts
let value: string | number;

value = "Shanmukasagar"; // ✅
value = 123;              // ✅
value = true;             // ❌ Error
```

### 🔸 2. Union in Function Parameters
```ts
function printId(id: string | number) {
  console.log("ID:", id);
}
```

### 🔸 3. Narrowing Union Types
```ts
function greet(user: string | string[]) {
  if (typeof user === "string") {
    console.log("Hello " + user.toUpperCase());
  } else {
    user.forEach(u => console.log("Hello " + u.toUpperCase()));
  }
}
```

### 🔸 4. Union of Object Types
```ts
type Admin = { role: "admin"; accessLevel: number };
type User = { role: "user"; email: string };

type Person = Admin | User;

const person1: Person = { role: "admin", accessLevel: 5 };
const person2: Person = { role: "user", email: "sagar@mail.com" };
```

### 🔸 5. Literal Union Types
```ts
type Status = "loading" | "success" | "error";

let currentStatus: Status = "loading"; // ✅
currentStatus = "failed"; // ❌ Error
```

---

## ✅ What is a Tuple?

A tuple is a fixed-length, ordered array where each element has a specific type and position.

### 🔸 1. Basic Tuple Example
```ts
let user: [string, number];

user = ["Sagar", 25];        // ✅ Correct
user = [25, "Sagar"];        // ❌ Wrong order
user = ["Sagar", 25, true];  // ❌ Too many items
```

### 🔸 2. Tuple in Functions
```ts
function getUser(): [string, number] {
  return ["Sagar", 25];
}

const [name, age] = getUser(); // name = string, age = number
```

### 🔸 3. Optional Tuple Elements
```ts
type UserInfo = [string, number?, boolean?];

const u1: UserInfo = ["Sagar"];
const u2: UserInfo = ["Sagar", 25];
const u3: UserInfo = ["Sagar", 25, true];
```

### 🔸 4. Named Tuples (for clarity)
```ts
type Response = [statusCode: number, message: string];

const res: Response = [200, "OK"];
```

### 🔸 5. Tuple vs Array

| Feature              | Tuple        | Array                      |
|----------------------|--------------|-----------------------------|
| 📐 Fixed Length      | ✅ Yes       | ❌ No                        |
| 🎯 Typed by Position | ✅ Yes       | ❌ All elements same type    |
| ✅ Use Case          | Return multiple values | Store list of same type |

---

## ✅ What is an Enum?

An enum lets you define a set of named constant values.

### 🔸 1. Basic Enum Example
```ts
enum Direction {
  Up,
  Down,
  Left,
  Right
}

let move: Direction = Direction.Up;
console.log(move); // 0 (starts from 0 by default)
```

### 🔸 2. Custom Enum Values
```ts
enum StatusCode {
  Success = 200,
  NotFound = 404,
  ServerError = 500
}

let code: StatusCode = StatusCode.NotFound;
console.log(code); // 404
```

### 🔸 3. String Enums
```ts
enum Status {
  Loading = "loading",
  Success = "success",
  Error = "error"
}

let state: Status = Status.Success;
console.log(state); // "success"
```

✅ Use string enums for readable values.

### 🔸 4. Enum in Conditions
```ts
enum Role {
  Admin,
  User,
  Guest
}

function checkRole(role: Role) {
  if (role === Role.Admin) {
    console.log("Access granted");
  } else {
    console.log("Access denied");
  }
}

checkRole(Role.Admin);
```

---

## 👨‍💻 Author

**Shanmukasagar**  
Full-stack MERN Developer | Passionate about TypeScript & clean code  
📫 [LinkedIn](https://www.linkedin.com/in/shanmukasagar/) 

---
