---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Operators in JS

::left::

| Operator | Meaning        |
| -------- | -------------- |
| +        | Addition       |
| -        | Subtraction    |
| \*       | Multiplication |
| /        | Division       |
| %        | Modulo         |
| =        | Assignment     |

::right::

### Increment / Decrement

```js {*|2|3|*}{lines:true,startLine:1}
let number = 10;
number++;
number--;
```
<hr>

### Built-in Variables

```js {*}{lines:true,startLine:1}
width;
height;
```
<hr>

### Modulo In Action

```js {*}{lines:true,startLine:1}
let randomNum = random(1,100);
if(randomNum%2==0){
    console.log("The random Number was Even");
} else {
    console.log("The random Number was Odd")
}
height;
```

<hr>