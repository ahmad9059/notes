#nodejs #backend #project
### Code

```js
const http = require("http");
const fs = require("fs");
const url = require("url");

const data = fs.readFileSync(`${__dirname}/dev-data/data.json`, "utf-8");
const dataObj = JSON.parse(data);
const server = http.createServer((req, res) => {
  const pathName = req.url;
  if (pathName === "/") {
    res.end("This is Home Page!");
  } else if (pathName === "/api") {
    res.writeHead(200, {
      "content-type": "application/json",
    });
    res.end(data);
  } else {
    res.writeHead(404, {
      "content-type": "text/html",
    });
    res.end("Page Not Found!");
  }
});

server.listen(8000, () => {
  console.log("Listening to request on Port 8000....");
});
```

---

## 📘 Theory of the Code

This Node.js script creates a simple HTTP server that handles **routing** and **serves JSON data** based on the request URL.

---

### 🔧 1. Importing Core Modules

```js
const http = require("http");
const fs = require("fs");
const url = require("url");
```

- `http`: Built-in module to create the server.
- `fs`: File System module to read files (like JSON).
- `url`: Useful for parsing URLs (though unused here, but helpful for future query/params handling).

---

### 📦 2. Reading the Data File

```js
const data = fs.readFileSync(`${__dirname}/dev-data/data.json`, "utf-8");
const dataObj = JSON.parse(data);
```

- `fs.readFileSync(...)`: Reads `data.json` synchronously at startup.
- `__dirname`: Gives the current directory path.
- `JSON.parse(...)`: Converts JSON string into a JavaScript object (`dataObj`) to be used later (even though `dataObj` isn’t used directly yet, it's parsed and ready).

---

### 🌐 3. Creating the HTTP Server

```js
const server = http.createServer((req, res) => {
  const pathName = req.url;
```

- `http.createServer(...)`: Creates the server.
- `req.url`: Extracts the route from the request (e.g., `/`, `/api`).

---

### 🧭 4. Routing Logic

#### ✅ Route: `/`

```js
if (pathName === "/") {
  res.end("This is Home Page!");
```

- Responds with simple text when the user visits `/`.

---

#### ✅ Route: `/api`

```js
} else if (pathName === "/api") {
  res.writeHead(200, {
   "content-type": "application/json",
  });
  res.end(data);
```

- Responds with the contents of `data.json`.
- `res.writeHead(200, ...)`: Sends an HTTP 200 status code with a `Content-Type` of `application/json`.
- `res.end(data)`: Sends the JSON as a response body.

---

#### ❌ All Other Routes (404)

```js
} else {
  res.writeHead(404, {
   "content-type": "text/html",
  });
  res.end("Page Not Found!");
```

- Any unknown route responds with a 404 status code.
- Sends a simple `"Page Not Found!"` message in HTML format.

---

### 🚀 5. Starting the Server

```js
server.listen(8000, () => {
  console.log("Listening to request on Port 8000....");
});
```

- Starts the server on `localhost:8000`.
- When started, it logs to the console: `"Listening to request on Port 8000...."`.

---

### 📊 Summary of Route Behavior

| Route      | Description                        | Content-Type           |
| ---------- | ---------------------------------- | ---------------------- |
| `/`        | Responds with home page message    | `text/plain` (default) |
| `/api`     | Returns JSON data from `data.json` | `application/json`     |
| other URLs | Shows `"Page Not Found!"` message  | `text/html`            |

---

### 💡 Notes

- The server is **synchronous**, so `fs.readFileSync` blocks the event loop at startup. This is fine here, but for high-scale apps, consider `fs.readFile` (async).
- This is a **foundation** for building REST APIs with routes like `/users`, `/products`, etc.
