---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---


# Quartiles & Interquartile Range  
## Understanding the Middle of the Data  

::left::

### Learning Goals

By the end of this lesson, you should be able to:

- Explain what **quartiles** are
- Describe the **interquartile range (IQR)**
- Understand why IQR is more robust than range
- Calculate quartiles and IQR in JavaScript
- Visualise quartiles using p5.js

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Why Go Beyond Range?

::left::
### Range only tells us:

- The **distance between extremes**

But extremes can be misleading.

Quartiles focus on:

- Where **most of the data lives**
- The **middle 50%** of values

---
hide: true
---

## What Are Quartiles?

Quartiles divide sorted data into **four equal parts**.

- **Q1** – 25% of values are below this
- **Q2** – The median (50%)
- **Q3** – 75% of values are below this


## Visual Idea

Think of data laid out on a number line:

~~~
|min----Q1----median----Q3----max|
~~~

Quartiles help us ignore extremes and focus on structure.


## Interquartile Range (IQR)

The **interquartile range** measures the spread of the middle 50%.

~~~
IQR = Q3 − Q1
~~~

Why it matters:

- Resistant to outliers
- Better description of typical spread


## Example Dataset

Consider this dataset:

~~~
[65, 70, 72, 74, 95]
~~~

Sorted:

~~~
[65, 70, 72, 74, 95]
~~~

- Q1 = 70  
- Median (Q2) = 72  
- Q3 = 74  
- IQR = 4  


## Realistic Data Structure

We usually start with **arrays of objects**.

~~~js
const students = [
  { name: "Alex", score: 65 },
  { name: "Beth", score: 70 },
  { name: "Carl", score: 72 },
  { name: "Dana", score: 74 },
  { name: "Evan", score: 95 }
];
~~~


## Step 1: Extract Numeric Values

~~~js
const scores = students.map(s => s.score);
~~~


## Step 2: Sort the Data

Quartiles require sorted values.

~~~js
function sortValues(values) {
  return [...values].sort((a, b) => a - b);
}
~~~


## Step 3: Calculate the Median (Reusable)

~~~js
function calculateMedian(values) {
  let middle = Math.floor(values.length / 2);

  if (values.length % 2 === 0) {
    return (values[middle - 1] + values[middle]) / 2;
  } else {
    return values[middle];
  }
}
~~~


## Step 4: Calculate Quartiles

~~~js
function calculateQuartiles(values) {
  let sorted = sortValues(values);
  let mid = Math.floor(sorted.length / 2);

  let lowerHalf = sorted.slice(0, mid);
  let upperHalf = sorted.length % 2 === 0
    ? sorted.slice(mid)
    : sorted.slice(mid + 1);

  let q1 = calculateMedian(lowerHalf);
  let q2 = calculateMedian(sorted);
  let q3 = calculateMedian(upperHalf);

  return { q1, q2, q3 };
}
~~~


## Step 5: Calculate IQR

~~~js
function calculateIQR(values) {
  let { q1, q3 } = calculateQuartiles(values);
  return q3 - q1;
}
~~~


## Step 6: Check Results

~~~js
let quartiles = calculateQuartiles(scores);
let iqr = calculateIQR(scores);

console.log(quartiles);
console.log("IQR:", iqr);
~~~

Always verify values before visualising.


## Visualisation Plan

We will draw:

- One bar per score
- Horizontal lines for:
  - Q1
  - Median
  - Q3
- A shaded region showing the IQR

| Statistic | Visual |
|---------|--------|
| Q1 | Lower horizontal line |
| Median | Middle line |
| Q3 | Upper line |
| IQR | Shaded band |


## p5.js: Setup

~~~js
let scores = [65, 70, 72, 74, 95];
let q1, q2, q3;

function setup() {
  createCanvas(600, 400);

  let qs = calculateQuartiles(scores);
  q1 = qs.q1;
  q2 = qs.q2;
  q3 = qs.q3;
}
~~~


## p5.js: Drawing Quartiles

~~~js
function draw() {
  background(240);

  let barWidth = width / scores.length;

  for (let i = 0; i < scores.length; i++) {
    let h = map(scores[i], 0, 100, 0, height);
    rect(i * barWidth, height - h, barWidth - 5, h);
  }

  let q1Y = map(q1, 0, 100, height, 0);
  let q2Y = map(q2, 0, 100, height, 0);
  let q3Y = map(q3, 0, 100, height, 0);

  // IQR band
  noStroke();
  fill(200, 220, 255);
  rect(0, q3Y, width, q1Y - q3Y);

  // Quartile lines
  stroke(0);
  line(0, q1Y, width, q1Y);
  line(0, q2Y, width, q2Y);
  line(0, q3Y, width, q3Y);

  noStroke();
  fill(0);
  text("Q1", 10, q1Y - 5);
  text("Median", 10, q2Y - 5);
  text("Q3", 10, q3Y - 5);
}
~~~


## Outlier Experiment

Change one value:

~~~
95 → 300
~~~

Questions:

- What changes?
- What stays the same?
- Why is IQR more stable than range?


## Interpretation

- Quartiles describe **distribution structure**
- IQR focuses on **typical spread**
- Outliers affect IQR far less than range


## Key Takeaway

Range looks at the **edges**.  
Quartiles look at the **middle**.

To understand data properly,  
you need **both**.
