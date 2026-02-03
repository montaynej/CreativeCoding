---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---


# Mean and Median
## Introduction to Statistics  

::left::

### Learning Goals

By the end of this lesson, you should be able to:

- Explain what **mean** and **median** are
- Describe when each is appropriate
- Calculate mean and median in JavaScript
- Work with arrays of objects
- Visualise statistics using p5.js

::right::

### What Is the Mean?

The **mean** (average):

- Add all values together
- Divide by how many values there are

It represents the **balancing point** of the data.

<br>

### What Is the Median?

The **median**:

- Sort the data
- Take the **middle value**

It represents a **typical value** and is less affected by extreme values.

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Why Do We Need Both?
## What do they tell us

::left::
Consider this dataset:

~~~
[10, 11, 12, 13, 1000]
~~~

- Mean = **209.2**
- Median = **12**

<br>

The mean is distorted by an **outlier**.  
The median reflects what is typical.

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

Result:
~~~
[65, 70, 72, 74, 95]
~~~

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Calculate the Mean & Median with JS
## Using the JS you have learnt to date

::left::
### Calculate the Mean
~~~js
function calculateMean(values) {
  let sum = 0;
  for (let v of values) {
    sum += v;
  }
  return sum / values.length;
}
~~~

::right::
### Step 3: Calculate the Median

~~~js
function calculateMedian(values) {
  let sorted = [...values].sort((a, b) => a - b);
  let middle = Math.floor(sorted.length / 2);

  if (sorted.length % 2 === 0) {
    return (sorted[middle - 1] + sorted[middle]) / 2;
  } else {
    return sorted[middle];
  }
}
~~~


## Key Takeaway

**Extract → Calculate → Visualise → Interpret**

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Implement the Mean & Median lines
## You need **both** to understand the data

::left::
### Final Chart


<div>
<img src="/images/Screenshot 2026-02-02 at 15.04.47.png" alt="Chart" style="width: 80%" />
</div>