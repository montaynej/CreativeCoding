---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Introduction to Arrays

## Arrays help us work with <strong>collections</strong> of values:

::left::

### Before Arrays

```js {*|1|5|*}{lines:true,startLine:1}
let score1 = 42;
let score2 = 55;
let score3 = 61;

console.log(score1, score2, score3);
```

❌ Hard to manage  
❌ Hard to loop  
❌ Hard to scale

<hr>

### With Arrays

```js
let scores = [42, 55, 61];
```

✅ One variable
✅ Easy to loop
✅ Perfect for visuals & games

::right::

### Creating an Array

```js
let colours = ["red", "blue", "green"];
```

Arrays use <strong>square brackets</strong>

<hr>

### Array Indexes

```js
let colours = ["red", "blue", "green"];
console.log(colours[0]);

returns - "red";
```

- Each item has an <strong>index</strong>
- Indexes start at <strong>0</strong>
- <strong>Array Methods we need to Know <span v-mark.circle.red>now:</span></strong>
- How to change item, delete an item, know the length, add an item (Start or End), Slicing, Finding

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Introduction to Arrays

::left::

### Use square brackets `[]`

```js {*|1|3|*}{lines:true,startLine:1}
let fruits = ["apple", "banana", "orange"];

console.log(fruits[0]); // apple
console.log(fruits[2]); // orange
```
<hr>

### Changing an Item



```js {*|3|5-6|*}{lines:true,startLine:1}
let fruits = ["apple", "banana", "orange"];

fruits[1] = "pear";

console.log(fruits);
// ["apple", "pear", "orange"]
```

You can overwrite a value using its index.

::right::

### Array Length



```js {*|3|*}{lines:true,startLine:1}
let fruits = ["apple", "banana", "orange"];

console.log(fruits.length); // 3
```

- The `.length` property tells you how many items are in an array.
- Useful when looping through arrays.

<hr>

### Adding Items – push()

`push()` adds an item to the **end**.

```js {*|3|5-6|*}{lines:true,startLine:1}
let fruits = ["apple", "banana"];

fruits.push("orange");

console.log(fruits);
// ["apple", "banana", "orange"]
```

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Introduction to Arrays Continued

::left::

### Removing Items – pop()

```js {*|3|*}{lines:true,startLine:1}
let fruits = ["apple", "banana", "orange"];

fruits.pop();

console.log(fruits);
// ["apple", "banana"]
```

`pop()` removes the **last** item.

<hr>

### Adding to the Start – unshift()

```js {*|3|*}{lines:true,startLine:1}
let fruits = ["banana", "orange"];

fruits.unshift("apple");

console.log(fruits);
// ["apple", "banana", "orange"]
```

::right::

### Removing from the Start – shift()

```js {*|3|*}{lines:true,startLine:1}
let fruits = ["apple", "banana", "orange"];

fruits.shift();

console.log(fruits);
// ["banana", "orange"]
```

<hr>

### Looping Through Arrays (for loop)

```js {*|3-5|*}{lines:true,startLine:1}
let fruits = ["apple", "banana", "orange"];

for (let i = 0; i < fruits.length; i++) {
	console.log(fruits[i]);
}
```

This is the **most common** pattern.

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Introduction to Arrays Continued

::left::

### Looping with for...of



```js {*|3-5|*}{lines:true,startLine:1}
let fruits = ["apple", "banana", "orange"];

for (let fruit of fruits) {
	console.log(fruit);
}
```

Cleaner syntax when you don’t need the index.

<hr>

### Finding Items – indexOf()

```js {*|3|*}{lines:true,startLine:1}
let fruits = ["apple", "banana", "orange"];

console.log(fruits.indexOf("banana")); // 1
console.log(fruits.indexOf("pear")); // -1
```

`-1` means **not found**.

<hr>

::right::

### Slicing Arrays – slice()



```js {*|3|*}{lines:true,startLine:1}
let fruits = ["apple", "banana", "orange", "pear"];

let citrus = fruits.slice(1, 3);

console.log(citrus);
// ["banana", "orange"]
```

`slice()` copies part of an array.

Original array stays the same.

<hr>

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Introduction to Arrays Continued

::left::

### Removing/Replacing – splice()



```js {*|3|*}{lines:true,startLine:1}
let fruits = ["apple", "banana", "orange"];

fruits.splice(1, 1);

console.log(fruits);
// ["apple", "orange"]
```

`splice()` **changes** the array.

<hr>

### Replacing with splice()

```js {*|3|*}{lines:true,startLine:1}
let fruits = ["apple", "banana", "orange"];

fruits.splice(1, 1, "pear");

console.log(fruits);
// ["apple", "pear", "orange"]
```

<hr>

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Exercise: Fruit Basket Manager

::left::

### Goal

- You are building a fruit basket manager for a small game.
- You will store fruit in an array and perform different operations on it.

<hr>

### Starting Code

```js
let basket = ["apple", "banana", "orange", "pear"];
```

<hr>

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Exercise: Fruit Basket Manager Tasks

::left::

### Read from the array

- Log the first fruit
- Log the last fruit (Hint: use .length)

<hr>

### Modify the basket

- Replace "banana" with "kiwi" (FInd Banana first)
- Remove the last fruit
- Add "mango" to the start of the array

<hr>

### Loop through the basket

- Use a for loop to log every fruit in this format:

```js
Fruit 1: apple
Fruit 2: kiwi
Fruit 3: orange
```

(Indexes start at 0, but your output should start at 1.)

<hr>

::right::

### Search for a fruit

- Check if "orange" exists in the basket
- If it exists, log: Orange found at index X
- If it doesn’t exist, log: Orange not found

<hr>

### Copy part of the basket

- Create a new array called citrus
- It should contain only the middle two fruits
- The original basket array must not change

<hr>

### Rules / Constraints

Students may only use:

- Arrays ([]), Indexing ([i]), .length, push, pop, shift, unshift, indexOf, slice, for loops, ❌ No map, filter, includes, or while

<hr>

---
layout: two-cols-header
hideInToc: true
---

# Solution

::left::
```js {1|3-5|7-11|13|14|16-19|21-27|29-33}{lines:true,startLine:1, maxHeight:'400px'}
let basket = ["apple", "banana", "orange", "pear"];

// 1️⃣ Read
console.log(basket[0]);
console.log(basket[basket.length - 1]);

// 2️⃣ Modify
let bananaIndex = basket.indexOf("banana");
if (bananaIndex !== -1) {
	basket[bananaIndex] = "kiwi";
}

basket.pop();
basket.unshift("mango");

// 3️⃣ Loop
for (let i = 0; i < basket.length; i++) {
	console.log(`Fruit ${i + 1}: ${basket[i]}`);
}

// 4️⃣ Search
let orangeIndex = basket.indexOf("orange");
if (orangeIndex !== -1) {
	console.log(`Orange found at index ${orangeIndex}`);
} else {
	console.log("Orange not found");
}

// 5️⃣ Slice
let middleStart = Math.floor((basket.length - 2) / 2);
let citrus = basket.slice(middleStart, middleStart + 2);

console.log(citrus);
```
