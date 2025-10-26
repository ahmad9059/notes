
## What is Lua?

Lua is a lightweight, embeddable scripting language designed for speed and portability. It is often used in game development, embedded systems, and as a configuration language.

### Common Use Cases

- Game scripting (e.g. Roblox, World of Warcraft)
- Configuration files (e.g. Neovim, Redis)
- Embedded systems and IoT
- Lightweight scripting inside C/C++ programs

---

## Comments in Lua

- One-line comment:

    ```lua
    -- This is a single-line comment
    ```

- Multi-line comment:

```lua
    --[[
      This is a
      multi-line comment
    --]]
```

---

## Variables & Flow Control

### Variable Declaration

```lua
num = 42          -- Numbers are float or int
s = 'hello'       -- String with single quotes
t = "world"       -- String with double quotes
u = [[Multi-line
       string]]
t = nil           -- t is undefined now
```

### While Loop

```lua
while num < 50 do
  num = num + 1
end
```

### If Statement

```lua
if num > 40 then
  print("over 40")
elseif s ~= 'test' then
  print("not over 40")
else
  local line = io.read()
  print("Hello, " .. line)
end
```

### Truthy/Falsy Values

```lua
if not false then print("false is falsy") end
-- Only `false` and `nil` are falsy. 0 and '' are truthy.
```

### Ternary Equivalent

```lua
result = condition and "yes" or "no"
```

### For Loop

```lua
sum = 0
for i = 1, 100 do
  sum = sum + i
end

-- Countdown
for i = 100, 1, -1 do
  sum = sum + i
end
```

### Repeat...Until

```lua
repeat
  print("looping...")
  num = num - 1
until num == 0
```

---

## Functions

### Simple Function

```lua
function fib(n)
  if n < 2 then return 1 end
  return fib(n - 1) + fib(n - 2)
end
```

### Closures

```lua
function adder(x)
  return function(y) return x + y end
end

add9 = adder(9)
print(add9(5))  -- 14
```

### Multiple Return Values

```lua
function foo()
  return 1, 2, 3
end

a, b = foo()  -- a=1, b=2
```

### Anonymous Function

```lua
square = function(x) return x * x end
```

### Function as Local Variable

```lua
local function f(x) return x * x end
-- or
local f; f = function(x) return x * x end
```

---

## Tables

### Dictionary Style (Associative Arrays)

```lua
t = {key1 = "val1", key2 = false}
print(t.key1)        -- val1
t.newKey = 123       -- Add new key
t.key2 = nil         -- Remove key
```

### Arbitrary Keys

```lua
u = {["$"] = "cash", [{}] = 1234, [3.14] = "pi"}
print(u[3.14])       -- pi
```

### Table Iteration

```lua
for k, v in pairs(u) do
  print(k, v)
end
```

### Using Tables as Lists

```lua
v = {"one", "two", "three"}
for i = 1, #v do
  print(v[i])
end
```

---

## Special Table: `_G`

- `_G` holds all global variables.
    

```lua
print(_G["_G"] == _G)  -- true
```

---

## Summary of Key Points

| Feature              | Syntax Example                             | One-liner Explanation                   |
| -------------------- | ------------------------------------------ | --------------------------------------- |
| Single-line comment  | `-- comment`                               | Uses two dashes                         |
| Multi-line comment   | `--[[ comment ]]`                          | Uses double brackets                    |
| String concat        | `'hello' .. 'world'`                       | Use `..` operator                       |
| Conditional          | `if cond then ... elseif ... else ... end` | Classic if-elseif-else                  |
| Loop                 | `for i=1,10 do ... end`                    | C-style for loop                        |
| Function             | `function name(args) ... end`              | Define function with `function` keyword |
| Anonymous function   | `f = function(x) return x end`             | First-class functions                   |
| Table creation       | `t = {key = value}`                        | Lua's only data structure               |
| List indexing        | `t[1]`                                     | 1-based indexing                        |
| Global scope default | `x = 5`                                    | All variables are global unless `local` |


## 3.1 Metatables and Metamethods

### What are Metatables?

Metatables allow you to change how tables behave with operators or field access, similar to operator overloading or prototypes.

---

### Operator Overloading Example: `__add`

```lua
f1 = {a = 1, b = 2}
f2 = {a = 2, b = 3}

metafraction = {}
function metafraction.__add(f1, f2)
  sum = {}
  sum.b = f1.b * f2.b
  sum.a = f1.a * f2.b + f2.a * f1.b
  return sum
end

setmetatable(f1, metafraction)
setmetatable(f2, metafraction)

s = f1 + f2  -- __add metamethod gets called
```

_One-liner:_ Metatables let tables respond to operators like `+`, `-`, etc. via metamethods.

---

### Dot Lookup Overloading: `__index`

```lua
defaultFavs = {animal = 'gru', food = 'donuts'}
myFavs = {food = 'pizza'}

setmetatable(myFavs, {__index = defaultFavs})
print(myFavs.animal)  -- Output: gru
```

_One-liner:_ `__index` allows fallback values when a key is not found in a table.

---

### `__index` as a Function

```lua
setmetatable(myFavs, {
  __index = function(tbl, key)
    return "unknown"
  end
})
print(myFavs.animal)  -- Output: unknown
```

_One-liner:_ You can use a function in `__index` for dynamic lookups.

---

### Common Metamethods

|Metamethod|Description|
|---|---|
|`__add(a,b)`|`a + b`|
|`__sub(a,b)`|`a - b`|
|`__mul(a,b)`|`a * b`|
|`__div(a,b)`|`a / b`|
|`__mod(a,b)`|`a % b`|
|`__pow(a,b)`|`a ^ b`|
|`__unm(a)`|`-a`|
|`__concat(a,b)`|`a .. b`|
|`__len(a)`|`#a`|
|`__eq(a,b)`|`a == b`|
|`__lt(a,b)`|`a < b`|
|`__le(a,b)`|`a <= b`|
|`__index(a,k)`|`a.k`|
|`__newindex(a,k,v)`|`a.k = v`|
|`__call(a,...)`|`a(...)`|

_One-liner:_ Metamethods let you redefine behavior for Lua operators and field access.

---

## 3.2 Class-like Tables & Inheritance

### Creating a Class in Lua

```lua
Dog = {}

function Dog:new()
  newObj = {sound = 'woof'}
  self.__index = self
  return setmetatable(newObj, self)
end

function Dog:makeSound()
  print('I say ' .. self.sound)
end

mrDog = Dog:new()
mrDog:makeSound()  -- Output: I say woof
```

_One-liner:_ Classes in Lua are simulated using tables and metatables.

---

### Explanation Breakdown

| Line | What it Does                                       |
| ---- | -------------------------------------------------- |
| 1    | `Dog` acts as a class (just a table)               |
| 2    | `Dog:new()` creates a new instance                 |
| 3    | `newObj` is the instance table                     |
| 4    | `self.__index = self` links methods via metatable  |
| 5    | `setmetatable()` binds the instance to the class   |
| 6-8  | Method call via colon `:` passes `self` implicitly |

---

### Inheritance Example

```lua
LoudDog = Dog:new()

function LoudDog:makeSound()
  local s = self.sound .. ' '
  print(s .. s .. s)
end

seymour = LoudDog:new()
seymour:makeSound()  -- Output: woof woof woof
```

_One-liner:_ Inheritance is done by chaining metatables and `__index`.

---

### Custom `new()` in Subclass

```lua
function LoudDog:new()
  newObj = {sound = "bark"}
  self.__index = self
  return setmetatable(newObj, self)
end
```

_One-liner:_ Subclasses can override `new()` to customize object creation.

---

Here’s your structured note on **Modules in Lua** with concise explanations and code examples, following the same clean format:

---

## What Are Modules?

Modules in Lua are files that return a table of functions or variables, allowing reusable and encapsulated code across files.

_One-liner:_ A module is just a Lua file that returns a table.

---

## Creating a Module

### `mod.lua`

```lua
local M = {}

local function sayMyName()
  print('Hrunkner')
end

function M.sayHello()
  print('Why hello there')
  sayMyName()
end

return M
```

_One-liner:_ The table `M` holds the public functions, while internal functions stay private.

---

## Using the Module

### Another File

```lua
local mod = require('mod')  -- Loads mod.lua
mod.sayHello()
-- Output:
-- Why hello there
-- Hrunkner
```

_One-liner:_ `require` loads and executes a module file, returning whatever it returns.

---

## Access Limitation

```lua
mod.sayMyName()  -- ❌ Error: sayMyName is local
```

📝 _One-liner:_ Only functions added to `M` are accessible outside the module.

---

## How `require` Works Internally

```lua
-- Rough equivalent:
local mod = (function ()
  -- contents of mod.lua
end)()
```

_One-liner:_ `require` wraps the module code in a function, so its locals stay private.

---

## `require` Caches Modules

```lua
-- mod2.lua
print("Hi!")

-- main.lua
local a = require("mod2")  -- Prints: Hi!
local b = require("mod2")  -- No output; uses cached result
```

_One-liner:_ Modules are loaded only once and cached by `require`.

---

## Other Ways to Load Files

### `dofile`

```lua
dofile('mod2.lua')  -- Runs it immediately
dofile('mod2.lua')  -- Runs again
```

_One-liner:_ `dofile` executes a file every time without caching.

---

### `loadfile`

```lua
f = loadfile('mod2.lua')  -- Loads but doesn't run
f()  -- Runs the loaded file
```

📝 _One-liner:_ `loadfile` reads a Lua file and returns a function.

---

### `load` (formerly `loadstring`)

```lua
g = load('print(343)')  -- Returns a function
g()  -- Prints: 343
```

📝 _One-liner:_ `load` compiles Lua code from a string and returns a runnable function.

---

## 🧾 Summary Table

|Function|Description|
|---|---|
|`require('mod')`|Loads, executes, and caches the result|
|`dofile('file')`|Loads and runs every time|
|`loadfile('file')`|Loads file and returns it as a function|
|`load('string')`|Loads Lua code from string, returns function|
