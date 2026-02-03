---
layout: image-left
image: /images/Screenshot%202026-01-26%20at%2020.55.07.png?raw=true
---

# Restructuring the Codebase

## We need to break out code into smaller functions

<br>

Lets begin by breaking the code into manageable chunks

- Function for the Axis
- Function for the Bars
- Function to clean the data
- Function to scale bars
- Update the draw() function

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Chart Functions

## Refactoring your code

::left::
Axis Function
```js {wrap:true}
function drawAxis() {
	noFill();
	stroke(axisColour);
	strokeWeight(axisThickness);
	// x-axis
	line(0, 0, chartWidth, 0);
	//y-axis
	line(0, 0, 0, -chartHeight);
}
```

::right::

Bars Function
```js {wrap:true}
function drawBars() {
	noStroke();
	fill(barColour);
	//prettier-ignore
	let barGap = (chartWidth - (barWidth * (numBars))) / (numBars + 1);

	push();
	translate(barGap, 0);
	for (let i = 0; i < numBars; i++) {
		// prettier-ignore
		let jump = (barGap * i) + (barWidth * i);
		let colHeight = scaler(cleanedData[i].Total);
		rect(jump, 0, barWidth, -colHeight);
	}
	pop();
}
```

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Chart Functions

## Refactoring your code

::left::
The Scale Function
```js {wrap:true}
function scaler(value) {
	let scaledValue = map(value, 0, maxValue, 0, chartHeight);
	return scaledValue;
}
```

::right::

The Clean Data Function
```js {wrap:true}
function cleanData() {
	for (let i = 0; i < data.rows.length; i++) {
		cleanedData.push({
			...data.rows[i].obj,
			Total: +data.rows[i].obj.Total,
			Female: +data.rows[i].obj.Female,
			Male: +data.rows[i].obj.Male,
		});
	}

	numBars = cleanedData.length;
	maxValue = max(cleanedData.map((row) => row.Total));
}
```

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Chart Functions

## Refactoring your code

::left::
The Setup Function
```js {wrap:true}
function setup() {
	createCanvas(canvasWidth, canvasHeight);
	cleanData();
	noLoop();
}
```

The Draw Function
```js
function draw() {
	background(backgroundColour);

	offsetX = (canvasWidth - chartWidth) / 2;
	offsetY = (canvasHeight - chartHeight) / 2 + chartHeight;

	translate(offsetX, offsetY);

	drawBars();
	drawAxis();
}
```

::right::
The Codebase
```js
function preload() {}

function setup() {}

function draw() {}

function cleanData() {}

function drawAxis() {}

function drawBars() {}

function scaler(value) {}
```

> Our code now is much easier to manage and develop