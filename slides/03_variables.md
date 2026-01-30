---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Variable in JS

::left::


### Variables — Anatomy

```js {*}{lines:true,startLine:1}
let h = 80;
```

- `let` → keyword
- `h` → variable name
- `80` → value

<hr>

```js {*}{lines:true,startLine:1}
let h = 80;
rect(20, 30, 50, h);
```

<hr>

### Variables — Reassigning

```js {*}{lines:true,startLine:1}
let h = 100;
rect(0, 0, 100, h);

h = 80;
rect(0, 0, 100, h);
```

::right::

### Variables — Calculations

```js {*}{lines:true,startLine:1}
let h = 100;
h = h * 2;
rect(0, 0, 100, h);
```
<hr>

### Debugging Tip

```js {*}{lines:true,startLine:1}
let x = 100;
console.log(x);
console.log("x is " + x);
```

<hr>