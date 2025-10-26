#backend #nodejs 
## 📂 `fs` Module in Node.js
---

- `fs` stands for **File System**.
- It's a **built-in Node.js module** used to interact with the file system.
- Provides **synchronous and asynchronous** methods to read, write, update, delete, and rename files and directories.
- No need to install — just `require('fs')`.


### Basic Syntax

```js
const fs = require("fs");
```


### Modes of Operation

Node's `fs` module supports two styles:

- **Synchronous (Blocking)**: `fs.readFileSync`, `fs.writeFileSync`, etc.
- **Asynchronous (Non-Blocking)**: `fs.readFile`, `fs.writeFile`, etc. (uses callbacks or can be used with Promises/async-await).


## Synchronous File Operations

These methods block the execution of further code until the current operation completes.

### 1.`fs.readFileSync(path, encoding)`

Reads a file **synchronously**.

```js
const data = fs.readFileSync('./txt/input.txt', 'utf-8');
console.log(data);
```

⚠️ If encoding is not specified, it returns a `Buffer` object instead of a string.


### 2.`fs.writeFileSync(path, data)` 

Writes data to a file synchronously. If the file does not exist, it's created. If it exists, it will be overwritten.

```js
const content = `This is new text added. \nOriginal: ${data}\nCreated on ${Date.now()}`;
fs.writeFileSync('./txt/output.txt', content);
```


### Example of Both Together

```js
const fs = require("fs");

const txtIn = fs.readFileSync("./txt/input.txt", "utf-8");
console.log(txtIn);

const txtOut = `This is new txt added; ${txtIn}.\nCreated on ${Date.now()}`;
fs.writeFileSync("./txt/output.txt", txtOut);

console.log("File Created!");
```


## Asynchronous File Operations (Better for Production)

These are **non-blocking**, and the rest of your code can run while the file operation is being performed.

### 1.`fs.readFile(path, encoding, callback)`

```js
fs.readFile('./txt/input.txt', 'utf-8', (err, data) => {
  if (err) return console.error('Error reading file:', err);
  console.log(data);
});
```

### 2.`fs.writeFile(path, data, callback)`

```js
fs.writeFile('./txt/output.txt', 'Some new content!', (err) => {
  if (err) return console.error('Error writing file:', err);
  console.log('File written successfully!');
});
```


## Common `fs` Methods Overview

|Method|Sync|Async|Description|
|---|---|---|---|
|`fs.readFileSync`|✅|❌|Read file contents (blocking)|
|`fs.readFile`|❌|✅|Read file contents (non-blocking)|
|`fs.writeFileSync`|✅|❌|Write to file (blocking)|
|`fs.writeFile`|❌|✅|Write to file (non-blocking)|
|`fs.appendFile`|❌|✅|Append data to file|
|`fs.unlink`|❌|✅|Delete a file|
|`fs.rename`|❌|✅|Rename or move a file|
|`fs.existsSync`|✅|❌|Check if a file exists|
|`fs.mkdir`|❌|✅|Create new directory|

## When to Use Sync vs Async?

- ✅ **Use Async** in production apps to avoid blocking the event loop.
- ⚙️ **Use Sync** only for scripting, setup files, or small utilities where performance isn't an issue.

## Check if File Exists

```js
if (fs.existsSync('./txt/input.txt')) {
  console.log('File exists!');
}
```


