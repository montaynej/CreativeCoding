---
layout: image-left
image: /barchart01.png
---

# Building a simple Barchart

## Using imported data values

- Firstly Declare some variables for the chart width and height, the canvas width height, the bar widths, and some colors
-  Create some blank Variables for your data and the number of bars. These can populated later or after loading your data
- Load your data and clean it
- Then we start thinking about drawing something

---
layout: image-left
image: /barchart01.png
hideInToc: true
---

# Building a simple Barchart

## Using imported data values

- Draw your axis first (from (0,0)) and use a translation to move to the centre of the screen
- Calculate your gaps
- Write a loop that will draw a rect at the correct intervals on the x-axis


---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# The Bar Chart Solution (Part 1)


::left::

```js {*}{lines:true,startLine:1, maxHeight:'430px'}
let data;
let cleanData = [];
let chartWidth = 400;
let chartHeight = 400;
let canvasWidth = 500;
let canvasHeight = 500;
let numBars;
let barWidth = 25;
let maxValue;

// Colours
let backgroundColour = "#e3e3e3";
let axisColour = "#474747";
let axisThickness = 3;
let barColour = "#416096";

function preload() {
	data = loadTable("data/Combined.csv", "csv", "header");
}


```

::right::

<div>
<img src="/barchart01.png" alt="Chart" style="width: 80%" />
</div>

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# The Bar Chart Solution (Part 2)


::left::

```js {*}{lines:true,startLine:1, maxHeight:'430px'}
function setup() {
	createCanvas(canvasWidth, canvasHeight);

	for (let i = 0; i < data.rows.length; i++) {
		cleanData.push({...data.rows[i].obj,
			Total:+data.rows[i].obj.Total,
			Female:+data.rows[i].obj.Female,
			Male:+data.rows[i].obj.Male
		});
	}
	//console.log(cleanData)
	numBars = cleanData.length;
	maxValue = max(cleanData.map(row => row.Total))
}

function draw() {
	background(backgroundColour);

	offsetX = (canvasWidth - chartWidth) / 2;
	//console.log(offsetX)
	offsetY = (canvasHeight - chartHeight) / 2 + chartHeight;
	//console.log(offsetY)


```

::right::

<div>
<img src="/barchart01.png" alt="Chart" style="width: 80%" />
</div>

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# The Bar Chart Solution (Part 3)


::left::

```js {*}{lines:true,startLine:1, maxHeight:'430px'}
	translate(offsetX, offsetY);
	noFill();
	stroke(axisColour);
	strokeWeight(axisThickness);
	// x-axis
	line(0, 0, chartWidth, 0);
	//y-axis
	line(0, 0, 0, -chartHeight);

	noStroke();
	fill(barColour);
	//prettier-ignore
	let barGap = (chartWidth - (barWidth * (numBars))) / (numBars + 1);
	// console.log(barGap);

```

::right::

<div>
<img src="/barchart01.png" alt="Chart" style="width: 80%" />
</div>

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# The Bar Chart Solution (Part 4)


::left::

```js {*}{lines:true,startLine:1, maxHeight:'430px'}
	
	push()
	translate(barGap,0)
	for (let i = 0; i < numBars; i++) {
		//prettier-ignore
		let jump = (barGap * i) + (barWidth * i);
		let colHeight = map(cleanData[i].Total,0,maxValue,0,chartHeight);
		rect(jump, 0, barWidth, -colHeight);
	}
	pop()
}


```

::right::

<div>
<img src="/barchart01.png" alt="Chart" style="width: 80%" />
</div>

