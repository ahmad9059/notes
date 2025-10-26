#backend #nodejs 
## 🌐 `http` Module in Node.js
---

The `http` module is a **core module** in Node.js that allows you to create HTTP servers and handle HTTP requests and responses.
- No need to install — it's built-in.
- Used to build **web servers**, **REST APIs**, and **microservices**.

### Importing the Module

```js
const http = require('http');
```


### Basic Server with `http.createServer()`

```js
http.createServer([options][, requestListener])
```

`requestListener` is a callback that handles every request.


### Basic Example

```js
const http = require('http');

const server = http.createServer((req, res) => {
  res.end("Hello From Server");
});

server.listen(8000, "127.0.0.1", () => {
  console.log("Listening to request on port 8000");
});
```


### The `req` (IncomingMessage) Object

Represents the HTTP **request**.

| Property         | Description                   |
| ---------------- | ----------------------------- |
| `req.url`        | The request URL               |
| `req.method`     | HTTP method (GET, POST, etc.) |
| `req.headers`    | Incoming headers              |
| `req.on('data')` | Listens to body data stream   |
| `req.on('end')`  | Marks end of data reception   |

### The `res` (ServerResponse) Object

Represents the HTTP **response**.

|Method|Description|
|---|---|
|`res.writeHead(statusCode, headers)`|Sets status & headers|
|`res.write(data)`|Sends a chunk of response data|
|`res.end([data])`|Ends the response|
|`res.setHeader(name, value)`|Set a specific header manually|
|`res.statusCode`|Set status code manually|

