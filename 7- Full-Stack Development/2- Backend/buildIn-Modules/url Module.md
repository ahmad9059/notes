#backend #nodejs 
## 🧭 Routing
---

**Routing** refers to how an application **handles incoming client requests** to different **URLs (routes)** and **HTTP methods** (like `GET`, `POST`, etc.).

In Node.js, routing allows your server to **respond differently based on the URL path** and the **request method** — much like how different pages of a website show different content.


### Example Concept

|Request URL|HTTP Method|Expected Response|
|---|---|---|
|`/`|`GET`|Show homepage|
|`/about`|`GET`|Show about page|
|`/submit`|`POST`|Accept form submission|
|`/api/products`|`GET`|Return JSON list of products|


## 🌐 Node.js `url` Module
---

The `url` module provides utilities for **parsing**, **constructing**, **resolving**, and **formatting** URL strings.

- Built-in Node.js module
- Commonly used when working with HTTP servers
- Useful for parsing `req.url` in custom servers (like with `http` module)


### Importing the Module

```js
const url = require('url');
```


### URL Parsing

```js
const { URL } = require('url');

const myUrl = new URL('https://example.com:8080/path/name?query=string#hash');

console.log(myUrl.hostname);  // 'example.com'
console.log(myUrl.pathname);  // '/path/name'
console.log(myUrl.search);    // '?query=string'
console.log(myUrl.hash);      // '#hash'
```



### Breakdown of a Parsed URL Object

```js
const myUrl = new URL('https://user:pass@example.com:8080/path/name?query=string#hash');
```


|Property|Value|
|---|---|
|`href`|Full URL string|
|`origin`|Protocol + hostname|
|`protocol`|`https:`|
|`username`|`user`|
|`password`|`pass`|
|`hostname`|`example.com`|
|`port`|`8080`|
|`pathname`|`/path/name`|
|`search`|`?query=string`|
|`searchParams`|URLSearchParams object|
|`hash`|`#hash`|


### Working with `searchParams`

`searchParams` is a powerful utility to handle query strings.

```js
const myUrl = new URL('https://example.com/search?term=node&sort=desc');

console.log(myUrl.searchParams.get('term')); // 'node'
console.log(myUrl.searchParams.has('sort')); // true

myUrl.searchParams.append('page', '2');
console.log(myUrl.toString()); // updated URL with ?page=2
```


### Formatting URLs

Use `url.format()` (for legacy-style URLs):

```js
const url = require('url');

const formattedUrl = url.format({
  protocol: 'https',
  hostname: 'example.com',
  pathname: '/docs',
  query: {
    q: 'nodejs'
  }
});

console.log(formattedUrl); // https://example.com/docs?q=nodejs
```


### Resolving Relative URLs

```js
const url = require('url');

const resolved = url.resolve('/docs', '/tutorial');
console.log(resolved); // '/tutorial'
```

Use `url.resolve()` when combining base and relative paths (mostly used in file paths or redirect logic).

### Example

```js
const server = http.createServer((req, res) => {
  if (req.url === "/" || req.url === "/home") {
    res.end("This is Home Page!");
  } else if (req.url === "/product") {
    res.end("Hello From PRODUCT!");
  } else if (req.url === "/category") {
    res.end("Hello From CATEGORY!");
  } else {
    res.writeHead(404, {
      "content-type": "text/html",
      "my-own-header": "hello world",
    });
    res.end("<h1>Page Not Found!</h1>");
  }
});

server.listen(8000, "127.0.0.1", () => {
  console.log("Listening to request on port 8000");
});
```

### Summary Table

| Feature               | Legacy API (`url.parse`) | Modern API (`new URL()`) |
| --------------------- | ------------------------ | ------------------------ |
| URL Parsing           | `url.parse(url)`         | `new URL(url)`           |
| URL Formatting        | `url.format(obj)`        | `url.toString()`         |
| Resolving URLs        | `url.resolve(from, to)`  | Manual via string ops    |
| Query Params Handling | Manual string parsing    | `URLSearchParams` object |

### 🧠 Best Practices

- ✅ Always prefer **`new URL()`** — modern, clean, and consistent
- ✅ Use `URLSearchParams` to handle query parameters
- ❌ Avoid using `url.parse()` and `url.resolve()` unless for legacy compatibility

