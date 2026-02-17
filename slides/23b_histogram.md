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
    if (index === binCount) {
      index = binCount - 1;
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