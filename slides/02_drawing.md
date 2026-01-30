---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Drawing in P5

## Creative coding with JavaScript

::left::

### What is p5.js?

> A JavaScript library for creative coding, based on Processing.

### Syntax

> The principles by which sentences are constructed in a particular language.

### Syntax — Plain English

> Draw a rectangle at the position x:20
> y:30 with the size of 50 x 80 pixels.

::right::

### Syntax — Code

```js {*}{lines:true,startLine:1}
rect(20, 30, 50, 80);
```

- **Function name:** `rect`
- **Parameters:** `x, y, w, h`

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Drawing in P5

::left::

### Drawing Functions

```js {*|1|2|3|4|*}{lines:true,startLine:1}
rect(x, y, w, h);
ellipse(x, y, w, h);
line(x1, y1, x2, y2);
point(x, y);

```

<hr>

### Style Functions

```js {*|1|2|3|*}{lines:true,startLine:1}
stroke(greyvalue);
fill(greyvalue);
strokeWeight(10);
```
<hr>

### Canvas

```js {*}{lines:true,startLine:1}
createCanvas(w, h);
```

<hr>

::right::

### Comments — Single Line

```js {*|1|*}{lines:true,startLine:1}
// draw rectangle
rect(20, 30, 50, 80);
```
<hr>

### Comments — Multi Line

```js {*|1-2|*}{lines:true,startLine:1}
/* draw
rectangle */
rect(20, 30, 50, 80);
```

<hr>
