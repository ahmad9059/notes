#web #backend #server #JavaScript #JS #nodejs #database 

## 1. What is Backend Development?
---
Backend development <mark style="background: #99E83E;">focuses on the server-side of web applications</mark>. It's responsible for:

- **Business logic** (rules and processes)
- **Database management**
- **User authentication/authorization**
- **API creation and integration**
- **Data validation and error handling**
- **Performance and scalability**

## 2. What is Node.js?
---
Node.js is a **JavaScript runtime environment** built on **Chrome's V8 engine**. It allows developers to run JavaScript **outside the browser**, on the server.

![|522x260](7-%20Full-Stack%20Development/2-%20Backend/assets/img.png)

## Why and When to Use Node.js?
---

### Why Use Node.js?

- Built on a **single-threaded**, **event-driven**, and **non-blocking I/O** architecture  
   → ideal for handling **multiple concurrent connections** efficiently.
- Enables creation of **fast**, **scalable**, and **real-time** applications       with high throughput.
- 🛠️ Uses **JavaScript on both frontend and backend**  
  → promotes **full-stack development** with a single language.
- Powered by **NPM (Node Package Manager)**  
   → access to one of the **largest open-source ecosystems**.
- Backed by a **huge developer community**  
   → continuous improvements, tutorials, and shared packages.
- Used in production by top companies:  
  `Netflix`, `Uber`, `PayPal`, `eBay`, `LinkedIn`, and more.
- **Cross-platform compatibility** for building desktop, CLI, or server apps.
- Designed for **I/O-bound tasks**, like APIs, file systems, and streaming.
### When to Use Node.js

Node.js is ideal for applications that are:

- **API-centric** with frequent database interaction   
  → works great with **NoSQL databases** (e.g., MongoDB).
- **Real-time applications**  
  → e.g., chat apps, messaging, multiplayer games (via WebSockets).
- **Streaming services**  
   → e.g., audio/video streaming apps, large file uploads.
- **Server-side rendered web applications**  
  → lightweight backend logic with fast response.
- **Microservices architecture**  
  → Node's modularity and performance make it a great fit.

### When _Not_ to Use Node.js

Avoid Node.js when your app requires
- **Heavy CPU-bound operations**  
  → Node's single-threaded nature struggles with:
  - Image/video processing
  - Complex mathematical computations
  - Machine learning or scientific tasks
- Better alternatives for CPU-intensive apps:
 - `Python` (with NumPy/Pandas), `Go`, `Rust`, `Java` or `C++`

**Note:** The Node.js <mark style="background: #99E83E;">REPL (Read-Eval-Print Loop)</mark> is an interactive shell environment that comes bundled with every Node.js installation. It allows users to execute JavaScript code directly in the terminal without needing to save it in a file first by running the `node` in terminal.

## Important Node.js Built-in Modules
---

| Module   | Purpose                     | Detailed Notes                                                                             |
| -------- | --------------------------- | ------------------------------------------------------------------------------------------ |
| `http`   | Create HTTP server          | [http Module](7-%20Full-Stack%20Development/2-%20Backend/buildIn-Modules/http%20Module.md) |
| `fs`     | File system interactions    | [fs Module](7-%20Full-Stack%20Development/2-%20Backend/buildIn-Modules/fs%20Module.md)     |
| `url`    | Parse, format, resolve URLs | [url Module](7-%20Full-Stack%20Development/2-%20Backend/buildIn-Modules/url%20Module.md)   |
| `path`   | Handle file paths           |                                                                                            |
| `os`     | OS-specific info            |                                                                                            |
| `crypto` | Handle encryption           |                                                                                            |
| `events` | Emit/listen to events       |                                                                                            |

## Building the Simple API 
---

Create an very simple API that give you data on specific route

<mark style="background: #C69AFF;">Detailed Explanation</mark> ->  [Building Simple API](7-%20Full-Stack%20Development/2-%20Backend/mini-projects/Building%20Simple%20API.md)


## Using Modules 2 – Our Own Modules
---
### Core Concept

In Node.js, **every file is treated as a module**. This means:

- You can define functions or values in one file,
- **Export** them,
- And **import** them into other files.

This promotes **code reuse**, **modularity**, and **clean structure** in your projects.


### Why Create Our Own Modules?

- You might use the same function (e.g., `replaceTemplate`) in multiple files.
- Instead of duplicating it, put it in a **separate file/module**.
- Then **export** it from there and **import** wherever needed.

### How to Create a Custom Module

1. Create a New File
   Example: `replaceTemplate.js`
2. Write Your Function

```js
module.exports = (temp, product) => {
  let output = temp.replace(…); // Your logic
  return output;
};
```

3. Import in Main File (index.js)

```js
const replaceTemplate = require('./replaceTemplate');
```

### Node.js Module System

- Each `.js` file is a **separate module**.
- Node.js modules can: 
  - **Export functions/objects/variables**
  - Be imported using `require()` (in CommonJS)
### Benefits
- Keeps your code **organized**
- Makes functions **reusable**
- Improves **maintainability**
