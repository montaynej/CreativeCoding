---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---


# Histograms & Binning
## Understanding Distributions  

::left::
### Learning Goals

By the end of this lesson, you should be able to:

- Explain what a **histogram** is
- Explain what **binning** means
- Choose a sensible number of bins (and know the trade-offs)
- Build a histogram from an array of objects in JavaScript
- Visualise a histogram in p5.js

::right::
<div>
<img src="/histogram.webp" alt="Chart" style="width: 80%" />
</div>


---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# What Is a Histogram?

::left::

## A histogram shows:

- How values are **distributed**
- By counting how many values fall into **ranges** (bins)

## It answers:

- Where are most values?
- Is the data clustered or spread out?
- Is it skewed left/right?
- Are there multiple “peaks”?

::right::

## Histogram vs Bar Chart

- A histogram is for **numeric ranges** (continuous data).

- A bar chart is for **categories** (discrete labels).

## Key visual clue:

- Histogram bars usually **touch** (ranges)
- Bar chart bars usually have **gaps** (categories)

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# What Is Binning?

::left::
## **Binning** means:

- Choose a bin width (or number of bins)
- Group values into ranges
- Count values per range

## Example bins (0–100, width 10):

~~~
0–10, 10–20, 20–30, ... 90–100
~~~
<br>

::right::
## Why Bin Choice Matters

### Too few bins:

- hides structure
- over-smooths the story

### Too many bins:

- looks noisy
- hard to interpret

### Goal:

- show shape without overfitting noise

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Example Dataset

::left::
We’ll use scores again:

~~~
[65, 70, 72, 74, 95, 40, 55, 61, 83, 88, 90, 33]
~~~

## Realistic Data Structure

~~~js
const students = [
  { name: "Alex", score: 65 },
  { name: "Beth", score: 70 },
  { name: "Carl", score: 72 },
  { name: "Dana", score: 74 },
  { name: "Evan", score: 95 },
  { name: "Faye", score: 40 },
  { name: "Gus", score: 55 },
  { name: "Hana", score: 61 },
  { name: "Ivo", score: 83 },
  { name: "Jia", score: 88 },
  { name: "Kai", score: 90 },
  { name: "Luz", score: 33 }
];
~~~

::right::

## Step 1: Extract Numeric Values

~~~js
const scores = students.map(s => s.score);
~~~


## Step 2: Choose Bin Settings

### We need:

- min value
- max value
- number of bins (or bin width)

### Lets start with:

- min = 0
- max = 100
- bins = 10  (width = 10)

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Example Dataset

::left::

### Step 3: Create Empty Bins

~~~js
createBins(binCount) {
  let bins = [];
  for (let i = 0; i < binCount; i++) {
    bins.push(0);
  }
  return bins;
}
~~~

### Step 4: Place Values Into Bins

We’ll map each value to a bin index:

~~~
index = floor((value - min) / binWidth)
~~~

Then we increment that bin.

::right::

## Histogram Function

~~~js
calculateBins(values, minValue, maxValue, binCount) {
  let bins = createBins(binCount);
  let binWidth = (maxValue - minValue) / binCount;

  for (let v of values) {
    // Ignore values outside range
    if (v < minValue || v > maxValue) continue;
    let index = Math.floor((v - minValue) / binWidth);

    // Edge case: maxValue should fall into last bin
    if (index === binCount) index = binCount - 1;

    bins[index] += 1;
  }

  return bins;
}
~~~

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Example Dataset

::left::


### Check Output

~~~js
let result = histogramCounts(scores, 0, 100, 10);
console.log(result);
~~~

::right::
### Example output might look like:

~~~
[0,0,0,1,1,1,2,3,2,2]
~~~

(Exact values depend on your data.)

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Labeling Bins (For Display)

::left::
### A bin label like:

~~~
60–70
~~~

is built from:

- start = min + i * binWidth
- end   = start + binWidth


### Bin Labels Function

~~~js
makeBinLabels(minValue, binWidth, binCount) {
  let labels = [];

  for (let i = 0; i < binCount; i++) {
    let start = minValue + i * binWidth;
    let end = start + binWidth;
    labels.push(`${Math.round(start)}–${Math.round(end)}`);
  }

  return labels;
}
~~~

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---


# What To Look For

::left::
### Ask students:

- Which bin is tallest?
- Is the shape symmetric or skewed?
- Are there gaps?
- Is there more than one peak?
- What structure disappears with 5 bins?
- What noise appears with 20 bins?
- Which tells the clearest story?


### Interpretation

- Histograms show **shape**
- Binning is a design choice
- Good bins reveal structure without exaggerating noise

::right::

### Key Takeaway

A histogram is:

# **values → bins → counts → shape**
## It’s one of the best ways to see what your data is “doing”.
