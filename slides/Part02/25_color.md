---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---


# Color - 01

::left::
<br>

## The ability to directly influence 16,777,216 colors gives users an amazing freedom. Simultaneous contrast—without which it would be impossible to perceive colors—is illustrated here by juxtaposing a number of color combinations. Our perception of a color is affected by its neighboring color and the shifting proportions of that color to its background.


::right::
<div>
<img src="/Gen_Images/color01_complete.jpg" alt="Chart" style="width: 90%" />
</div>

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---


# Color - 01

::left::
<br>

## The horizontal position of the mouse controls the size of the color field. Starting in the center, the colored area is depicted with a height and width of 1 to 720 pixels. The vertical mouse position controls the hue. The background passes through the color spectrum from 0 to 360, while the color field passes through the spectrum in the opposite direction, from 360 to 0.


::right::
<div>
<img src="/Gen_Images/color01_Diagram.jpg" alt="Chart" style="width: 90%" />
</div>

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hide: true
hideInToc: true
---


# Color - 01
## Changing Colors based on MouseX and MouseY



```js
function setup() {
	createCanvas(700, 700);
	//noCursor();

	colorMode(HSB, width, 100, 100);
	rectMode(CENTER);
	noStroke();
}

function draw() {
	my = constrain(mouseX, 0, width);

	background(my, 100, 100);

	push();
	translate(width / 2, height / 2);
	fill(width - my, 100, 100);
	rect(0, 0, mouseX + 1, mouseX + 1);
	pop();
}

function keyPressed() {
	if (key == "s" || key == "S") saveCanvas(gd.timestamp(), "png");
}
```

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---


# Color & Grids - 02
## Introducion

::left::
<br>

## This color spectrum is composed of colored rectangles. Each tile is assigned a hue on the horizontal axis and a saturation value on the vertical. The color resolution can be reduced by enlarging the rectangles so that the primary colors in the spectrum become clearer.


::right::
<div>
<img src="/color/grid.png" alt="Chart" style="width: 90%" />
</div>

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---


# Color & Grids - 02
## The Rules

::left::
<br>

## The grid is created by two nested for loops. In the outer loop, the y-position is increased, step by step. The inner loop then draws a line by increasing the value for the rectangle’s x-position, step by step, until the entire width is processed. The step size is set by the value of the mouse position and is located in the variables stepX and stepY. It also determines the length and width of the rectangles.


::right::
<div>
<img src="/Gen_Images/color02_diagram.jpg" alt="Chart" style="width: 90%" />
</div>

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hide: true
hideInToc: true
---


# Color & Grids - 02
## The Solution



```js {*} {lines:true,startLine:1, maxHeight:'400px'}
let stepX;
let stepY;

function setup() {
	createCanvas(800, 400);
	noStroke();
	colorMode(HSB, width, height, 100);
}

function draw() {
	stepX = mouseX + 2;
	stepY = mouseY + 2;

	for (let gridY = 0; gridY < height; gridY += stepY) {
		for (let gridX = 0; gridX < width; gridX += stepX) {
			fill(gridX, height - gridY, 100);
			rect(gridX, gridY, stepX, stepY);
		}
	}
}

function keyPressed() {
	if (key == "s" || key == "S") saveCanvas(gd.timestamp(), "png");
}

```

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---


# Radial Colors - 03
## Introduction

::left::
<br>

## There are numerous models for organizing colors. The color spectrum arranged in a circle (a color wheel) is a popular model for comparing harmonies, contrasts, and color tones. You can control the number of circle segments, as well as their brightness and saturation values, allowing you to better understand the color arrangement in HSB mode.


::right::
<div>
<img src="/color/radial.png" alt="Chart" style="width: 90%" />
</div>

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---


# Radial Colors - 03
## The Rules

::left::
<br>

## The color-wheel segments are arranged in the shape of a fan. The individual vertices are computed from the cosine and sine values of the corresponding angle. A Processing method mode can be used that makes it especially easy to create the wheel segments. The individual points have to be set in the following order: first the middle point, and then the outer ones sequentially.


::right::
<div>
<img src="/Gen_Images/color03_diagram.jpg" alt="Chart" style="width: 90%" />
</div>



---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hide: true
hideInToc: true
---


# Radial Colors - 03
## The Solution



```js {*} {lines:true,startLine:1, maxHeight:'400px'}
let segmentCount = 36;
let radius = 300;

function setup() {
	createCanvas(800, 800);
	noStroke();
	angleMode(DEGREES);
}

function draw() {
	colorMode(HSB, 360, width, height);
	background(360, 0, height);

	let angleStep = 360 / segmentCount;

	push();
	translate(width / 2, height / 2);
	beginShape(TRIANGLE_FAN);
	vertex(0, 0);

	for (let angle = 0; angle <= 360; angle += angleStep) {
		let vx = cos(angle) * radius;
		let vy = sin(angle) * radius;
		vertex(vx, vy);
		fill(angle, mouseX, mouseY);
	}

	endShape();
	pop();
}

function keyPressed() {
	if (key == "s" || key == "S") saveCanvas(gd.timestamp(), "png");

	switch (key) {
		case "1":
			segmentCount = 360;
			break;
		case "2":
			segmentCount = 45;
			break;
		case "3":
			segmentCount = 24;
			break;
		case "4":
			segmentCount = 12;
			break;
		case "5":
			segmentCount = 6;
			break;
	}
}

```



---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---


# Color Interpolation - 04
## Introduction

::left::
<br>

## In each color model, colors have their clearly defined place. The direct path from one color to another always has precisely definable gradations, which will vary depending on the specific model. Using this interpolation you can create color groups in every gradation, as well as locate individual intermediate nuances.


::right::
<div>
<img src="/color/interpol02.png" alt="Chart" style="width: 90%" />
</div>

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---


# Color Interpolation - 04
## The Rules

::left::
<br>

## Because a color is not defined by a single number but by several values, it is necessary to interpolate between these values. Depending on the chosen color model, RGB or HSB, the same color is defined by different values, thereby causing the path from one to another to lead past different colors. In the HSB color model, for instance, a detour is made past the color wheel. This difference is due to the characteristics of the color models, both of which can be very useful, depending on the situation. It is therefore important to choose the appropriate color model to solve a specific problem.


::right::
<div>
<img src="/Gen_Images/color04_diagram.jpg" alt="Chart" style="width: 90%" />
</div>

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hide: true
hideInToc: true
---


# Color Interpolation - 04
## The Solution Part A



```js {*} {lines:true,startLine:1, maxHeight:'400px'}
let tileCountX = 2;
let tileCountY = 10;

let colorsLeft = [];
let colorsRight = [];

function setup() {
	createCanvas(800, 800);
	colorMode(HSB);
	noStroke();
	shakeColors();
}

function draw() {
	tileCountX = int(map(constrain(mouseX, 0, width), 0, width, 2, 100));
	tileCountY = int(map(constrain(mouseY, 0, height), 0, height, 2, 10));
	let tileWidth = width / tileCountX;
	let tileHeight = height / tileCountY;
	let interCol;

	for (let gridY = 0; gridY < tileCountY; gridY++) {
		let col1 = colorsLeft[gridY];
		let col2 = colorsRight[gridY];

		for (let gridX = 0; gridX < tileCountX; gridX++) {
			let amount = map(gridX, 0, tileCountX - 1, 0, 1);
			interCol = lerpColor(col1, col2, amount);

			fill(interCol);

			let posX = tileWidth * gridX;
			let posY = tileHeight * gridY;

			push();
			translate(posX, posY);
			rect(0, 0, tileWidth, tileHeight);
			pop();
		}
	}
}

function shakeColors() {
	for (let i = 0; i < tileCountY; i++) {
		colorsLeft[i] = color(random(0, 60), random(0, 100), 100);
		colorsRight[i] = color(random(160, 190), 100, random(0, 100));
	}
}

function mouseReleased() {
	shakeColors();
}

function keyPressed() {
	if (key == "c" || key == "C")
		writeFile([gd.ase.encode(colors)], gd.timestamp(), "ase");
	if (key == "s" || key == "S") saveCanvas(gd.timestamp(), "png");
	if (key == "1") interpolateShortest = true;
	if (key == "2") interpolateShortest = false;
}

```



---
layout: cover
background: /color/interpol.png
---

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---


# Color Rules - 05
## Introduction

::left::
<br>

## All colors are made up of three components: hue, saturation, and brightness. The values for these color components are defined using a set of rules. By using controlled random functions, you can quickly create different palettes in specific color nuances.


::right::
<div>
<img src="/Gen_Images/P_1_2_3_01.png" alt="Chart" style="width: 90%" />
</div>

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---


# Color Rules - 05
## Introduction

::left::
<br>

## All colors are made up of three components: hue, saturation, and brightness. The values for these color components are defined using a set of rules. By using controlled random functions, you can quickly create different palettes in specific color nuances.


::right::
<div>
<img src="/color/colorPatterns01.png" alt="Chart" style="width: 90%" />
</div>


---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---



# Color Rules - 05
## Introduction

::left::
<br>

## All colors are made up of three components: hue, saturation, and brightness. The values for these color components are defined using a set of rules. By using controlled random functions, you can quickly create different palettes in specific color nuances.


::right::
<div>
<img src="/color/colorPatterns03.png" alt="Chart" style="width: 90%" />
</div>


---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---


# Color Rules - 05
## The Rules

::left::
<br>

## Values for hue, saturation, and brightness are randomly selected from predefined ranges of values. This combination of rule sets—the definition of value ranges—and random functions means that new palettes are continually created and that they always produce specific color nuances.

## Because the perception of color depends on context, the produced colors are drawn in an interactive grid. Even the color nuances emerge more distinctly.

::right::
<div>
<img src="/Gen_Images/color05_diagram.jpg" alt="Chart" style="width: 90%" />
</div>

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hide: true
hideInToc: true
---


# Color Rules - 05
## The Solution 



```js {*} {lines:true,startLine:1, maxHeight:'400px'}
let tileCountX = 2;
let tileCountY = 2;
let maxTileX = 50;
let maxTileY = 10;
let numColors = 25;

let hueValues = [];
let saturationValues = [];
let brightnessValues = [];

function setup() {
	createCanvas(windowWidth, windowHeight);
	colorMode(HSB, 360, 100, 100, 100);
	noStroke();

	// init with random values
	for (let i = 0; i < numColors; i++) {
		hueValues[i] = random(360);
		saturationValues[i] = random(100);
		brightnessValues[i] = random(100);
	}
}

function draw() {
	// white back
	background(0, 0, 100);

	// limit mouse coordinates to canvas
	let mX = constrain(mouseX, 0, width);
	let mY = constrain(mouseY, 0, height);

	// tile counter
	let counter = 0;

	// map mouse to grid resolution
	tileCountX = int(map(mX, 0, width, 1, maxTileX));
	tileCountY = int(map(mY, 0, height, 1, maxTileY));
	let tileWidth = width / tileCountX;
	let tileHeight = height / tileCountY;

	for (let y = 0; y < tileCountY; y++) {
		for (let x = 0; x < tileCountX; x++) {
			let posX = tileWidth * x;
			let posY = tileHeight * y;

			let index = counter % numColors;

			// get component color values
			fill(hueValues[index], saturationValues[index], brightnessValues[index]);
			rect(posX, posY, tileWidth, tileHeight);
			counter++;
		}
	}
}

function keyPressed() {
	if (key == "s" || key == "S") saveCanvas(gd.timestamp(), "png");
	if (key == "c" || key == "C") {
		// -- save an ase file (adobe swatch export) --
		let colors = [];
		for (let i = 0; i < hueValues.length; i++) {
			colors.push(
				color(hueValues[i], saturationValues[i], brightnessValues[i]),
			);
		}
		writeFile([gd.ase.encode(colors)], gd.timestamp(), "ase");
	}

	if (key == "1") {
		for (let i = 0; i < numColors; i++) {
			hueValues[i] = random(360);
			saturationValues[i] = random(100);
			brightnessValues[i] = random(100);
		}
	}

	if (key == "2") {
		for (let i = 0; i < numColors; i++) {
			hueValues[i] = random(360);
			saturationValues[i] = random(100);
			brightnessValues[i] = 100;
		}
	}

	if (key == "3") {
		for (let i = 0; i < numColors; i++) {
			hueValues[i] = random(360);
			saturationValues[i] = 100;
			brightnessValues[i] = random(100);
		}
	}

	if (key == "4") {
		for (let i = 0; i < numColors; i++) {
			hueValues[i] = 0;
			saturationValues[i] = 0;
			brightnessValues[i] = random(100);
		}
	}

	if (key == "5") {
		for (let i = 0; i < numColors; i++) {
			hueValues[i] = 195;
			saturationValues[i] = 100;
			brightnessValues[i] = random(100);
		}
	}

	if (key == "6") {
		for (let i = 0; i < numColors; i++) {
			hueValues[i] = 195;
			saturationValues[i] = random(100);
			brightnessValues[i] = 100;
		}
	}

	if (key == "7") {
		for (let i = 0; i < numColors; i++) {
			hueValues[i] = random(180);
			saturationValues[i] = random(80, 100);
			brightnessValues[i] = random(50, 90);
		}
	}

	if (key == "8") {
		for (let i = 0; i < numColors; i++) {
			hueValues[i] = random(180, 360);
			saturationValues[i] = random(80, 100);
			brightnessValues[i] = random(50, 90);
		}
	}

	if (key == "9") {
		for (let i = 0; i < numColors; i++) {
			if (i % 2 == 0) {
				hueValues[i] = random(360);
				saturationValues[i] = 100;
				brightnessValues[i] = random(100);
			} else {
				hueValues[i] = 195;
				saturationValues[i] = random(100);
				brightnessValues[i] = 100;
			}
		}
	}

	if (key == "0") {
		for (let i = 0; i < tileCountX; i++) {
			if (i % 2 == 0) {
				hueValues[i] = 140;
				saturationValues[i] = random(30, 100);
				brightnessValues[i] = random(40, 100);
			} else {
				hueValues[i] = 210;
				saturationValues[i] = random(40, 100);
				brightnessValues[i] = random(50, 100);
			}
		}
	}
}

```
