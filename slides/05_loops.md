---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Loops
## Repeating code automatically.

::left::
### While Loop

```js {*}{lines:true,startLine:1}
let i = 0;
while (i < 10) {
	rect(i * 80, 50, 50, 50);
	i = i + 1;
}
```

You need to increment the i within the while loop

<hr>

### For Loop

```js {*}{lines:true,startLine:1}
for (let i = 0; i < 10; i++) {
	rect(i * 80, 50, 50, 50);
}
```

The Increment is setup to change in the for statement
<hr>

::right::

<div>
<carbon:loop style="font-size: 348px; margin-top:10px; color: orange;" />
</div>
