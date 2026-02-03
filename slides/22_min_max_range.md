---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Min, Max & Range
## Understanding Spread in Data  

### Learning Goals

By the end of this lesson, you should be able to:

- Explain what **minimum**, **maximum**, and **range** are
- Describe why **spread** matters, not just averages
- Calculate min, max, and range in JavaScript
- Work with arrays of objects
- Visualise data spread using p5.js

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Why Spread Matters

## Two datasets can have the **same mean** but feel **very different**.

::left::
Spread helps us understand:

- How varied the data is
- Whether values are tightly grouped or far apart
- How extreme the extremes are

::right::
## Definitions

### Minimum (Min)
- The **smallest** value in a dataset

### Maximum (Max)
- The **largest** value in a dataset

### Range
- The distance between min and max

~~~
range = max − min
~~~

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Example Dataset


::left::
### Consider this data:
~~~
[65, 70, 72, 74, 95]
~~~

- Min = **65**
- Max = **95**
- Range = **30**

::right::
### Realistic Data Structure

We usually work with **arrays of objects**, not raw numbers.


~~~js
const students = [
  { name: "Alex", score: 65 },
  { name: "Beth", score: 70 },
  { name: "Carl", score: 72 },
  { name: "Dana", score: 74 },
  { name: "Evan", score: 95 }
];
~~~

### Step 1: Extract Numeric Values

~~~js
const scores = students.map(s => s.score);
~~~

### Result:

~~~
[65, 70, 72, 74, 95]
~~~

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Example Dataset

::left::
### Step 2: Calculate the Minimum

~~~js
function calculateMin(values) {
  let min = values[0];

  for (let v of values) {
    if (v < min) {
      min = v;
    }
  }

  return min;
}
~~~

::right::
### Step 3: Calculate the Maximum

~~~js
function calculateMax(values) {
  let max = values[0];

  for (let v of values) {
    if (v > max) {
      max = v;
    }
  }

  return max;
}
~~~

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Example Dataset

::left::
### Step 4: Calculate the Range

~~~js
function calculateRange(values) {
  let min = calculateMin(values);
  let max = calculateMax(values);
  return max - min;
}
~~~


### Step 5: Check Your Results

~~~js
let minScore = calculateMin(scores);
let maxScore = calculateMax(scores);
let rangeScore = calculateRange(scores);

console.log("Min:", minScore);
console.log("Max:", maxScore);
console.log("Range:", rangeScore);
~~~

Always verify values **before** visualising.

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Visualisation Plan

::left::
### We will show:

- One bar per score
- A **line at the minimum**
- A **line at the maximum**
- The **distance between them** as the range

::right::
| Data | Visual Mapping |
|----|----|
| Score | Bar height |
| Min | Bottom reference line |
| Max | Top reference line |
| Range | Distance between lines |

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Observations
## What Should You Notice?

::left::
- How far apart are min and max?
- Are most values near one end?
- Does the range describe the data well?




::right::
### Outlier Experiment

Change one value:

~~~
95 → 300
~~~

### Questions:

- What happens to the max?
- What happens to the range?
- Does range still describe “most” of the data?


### Interpretation

- Min and max show **extremes**
- Range is simple but **very sensitive to outliers**
- Range alone does not describe the full distribution

