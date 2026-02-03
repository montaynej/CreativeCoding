---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Applying Class & Object to the Bar Chart

## A simple example

::left::
Firstly, we define the properties of the chart


```js 
class BarChart {
	constructor() {
		this.data;
		this.cleanedData = [];
		this.chartWidth = 400;
		this.chartHeight = 400;
		this.barWidth = 25;
		this.maxValue;
		this.numBars;

		// Colours
		this.axisColour = "#474747";
		this.axisThickness = 3;
		this.barColour = "#416096";
	}
}
```


::right::

Lets prepare it for Parameters
```js
class BarChart {
	constructor(_data, _cWidth, _cHeight, _barWidth) {
		this.data = _data;
		this.cleanedData = [];
		this.chartWidth = _cWidth;
		this.chartHeight = _cHeight;
		this.barWidth = _barWidth;
		this.maxValue;
		this.numBars;

		// Colours
		this.axisColour = "#474747";
		this.axisThickness = 3;
		this.barColour = "#416096";
	}
}
```

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Applying Class & Object to the Bar Chart

## A simple example

::left::
Now lets add a method that will clean the data


```js {wrap:true}
class BarChart {
	constructor() {...}

	cleanData(){
		for (let i = 0; i < this.data.rows.length; i++) {
			this.cleanedData.push({
				...this.data.rows[i].obj,
				Total: +this.data.rows[i].obj.Total,
				Female: +this.data.rows[i].obj.Female,
				Male: +this.data.rows[i].obj.Male,
			});
		}

		this.numBars = this.cleanedData.length;
		this.maxValue = max(this.cleanedData.map((row) => row.Total));
	}
}
```


::right::

Our Main Sketch.js file now only has these variables
```js
let data;
let chart;
let canvasWidth = 500;
let canvasHeight = 500;
let backgroundColour = "#e3e3e3";
```

And our setup() looks like this

```js
function setup() {
	createCanvas(canvasWidth, canvasHeight);
	// cleanData();
	chart = new BarChart(data, 200, 200, 25);
	chart.cleanData();
	noLoop();
}
```

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Applying Class & Object to the Bar Chart

## A simple example


::left::

Now lets add a render method that will call draw methods


```js {wrap:true}
class BarChart {
	constructor() {...}

	cleanData(){}

	render() {
		push();
		translate(this.posX, this.posY);
		this.cleanData();
		this.drawAxis();
		pop();
	}
	drawAxis() {
		noFill();
		stroke(this.axisColour);
		strokeWeight(this.axisThickness);
		line(0, 0, this.chartWidth, 0);
		line(0, 0, 0, -this.chartHeight);
	}
}
```




::right::

Our Main Sketch.js file now only has these variables
```js
function setup() {
	createCanvas(canvasWidth, canvasHeight);
	chart = new BarChart(data, 50, 300, 200, 200, 25);

	noLoop();
}

function draw() {
	background(backgroundColour);
	chart.render();
}
```

Everything now is much tidier

<br>

> Make sure to add posX and posY to both constructor and to the parameter

