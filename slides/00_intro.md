---
layout: image-left
image: https://github.com/montaynej/Images-for-Slides/blob/main/Screenshot%202026-01-16%20at%2014.28.56.png?raw=true
---

# What we need to know?

## Arrays help us work with <strong>collections</strong> of values:

<br>

<v-clicks>

- <span v-mark.underline.red>Arrays</span>
- Variables
- Basic Drawing in p5
- Modes like AngleMode and RectMode
- Translations (<span v-mark.underline.red>really Important</span>)
- Loops within <span v-mark.circle.red>Loops</span>
- Basic <span v-mark.underline.red>Maths</span> Calculations to create a grid structure

</v-clicks>

---

# What it looks like!

## The Code Base

```js {*|1-5|7|9-14|17-18|20-21|23-45} {lines:true,startLine:1, maxHeight:'400px'}
let cols = 10;
let rows = 10;
let cellSize = 40;
let gridWidth = cols * cellSize;
let gridHeight = rows * cellSize;

let colors = [.....];

function setup() {
	createCanvas(500, 500);
	background(55, 0, 0);
	noStroke();
	angleMode(RADIANS);
	rectMode(CENTER);

	// centre the grid on the canvas
	let offsetX = (width - gridWidth) / 2;
	let offsetY = (height - gridHeight) / 2;

	push();
	translate(offsetX, offsetY);

for (let y = 0; y < rows; y++) {
		for (let x = 0; x < cols; x++) {
			let cx = x * cellSize + cellSize / 2;
			let cy = y * cellSize + cellSize / 2;

			let index = (x + y) % colors.length;
			let rotation = random(TWO_PI);

			push();
			translate(cx, cy);
			noFill();
			stroke(100);
			rect(0, 0, cellSize);

			rotate(rotation);
			noStroke();
			fill(colors[index]);

			ellipse(0, 0, cellSize * random(0.3, 1.2));

			pop();
		}
	}
	pop();
}
```
