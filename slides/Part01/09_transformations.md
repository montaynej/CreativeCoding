---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Transformations

## Manipulating the coordinate system.


::left::
### Transformation Functions

```js {*|3|*}{lines:true,startLine:1}
translate(x, y);
rotate(angle);
scale();
push();
pop();
```


### Rotation

```js {*|3|*}{lines:true,startLine:1}
rotate(radians(45));
rect(25, 25, 150, 25);
```

- Angle is in radians  
- Range: 0 → TWO_PI  
- Angle is in Degrees
- Range is 0 → 360

You can set angleMode(DEGREES) in Setup() if you prefer

::right::
### Translation

```js {*|3|*}{lines:true,startLine:1}
translate(50, 50);
rect(25, 25, 50, 100);
```

### Order Matters

Changing the order of `rotate()` and `translate()` changes the result.


### push() and pop()

```js {*|3|*}{lines:true,startLine:1}
push();
rotate(radians(45));
rect(25, 25, 150, 25);
pop();

rect(25, 25, 150, 25);
```

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Rotation

## Understanding the coordinate system


::left::
<div>
<img src="/translation01.png" alt="Chart" style="width: 80%" />
</div>

::right::
# rect(25,25,150,25);

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Rotation

## Understanding the coordinate system


::left::
<div>
<img src="/translation02.png" alt="Chart" style="width: 80%" />
</div>

::right::
# rotate(radians(45));
<br>

# rect(25,25,150,25);

<br>
rotate() rotates the coordinate system

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Translate

## Moves the coordinate system


::left::
<div>
<img src="/translation_Move.png" alt="Chart" style="width: 80%" />
</div>

::right::

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Translate

## Moves the coordinate system


::left::
<div>
<img src="/translation_Move.png" alt="Chart" style="width: 80%" />
</div>

::right::
# rect(25, 25, 50, 100);

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Translate

## Moves the coordinate system


::left::
<div>
<img src="/translation_Move.png" alt="Chart" style="width: 80%" />
</div>

::right::
# translate(50, 50)
<br>

# rect(25, 25, 50, 100);

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Translate

## Moves the coordinate system


::left::
<div>
<img src="/translation_move_move.png" alt="Chart" style="width: 80%" />
</div>

::right::
# translate(50, 50)
<br>

# rect(25, 25, 50, 100);
<br>

# translate(50, 50)
<br>

# rect(25, 25, 50, 100);

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Translate & Rotate

## Visualise the difference

::left::
<div>
<img src="/translation_rotate_move.png" alt="Chart" style="width: 80%" />
</div>

::right::

# <span style="color: white;"> rotate(radians(45));</span>
<br>

# <span style="color: white;">rect(25,25,150,25);</span>
<br>

# <span style="color: white;">translate(125, 50);</span>
<br>

# <span style="color: white;">rect(25,25,150,25);</span>
<br>




---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Translate & Rotate

## When changing the order

::left::
<div>
<img src="/translation_move_rotate.png" alt="Chart" style="width: 80%" />
</div>

::right::

# <span style="color: white;">translate(125, 50);</span>
<br>

# <span style="color: white;">rect(25,25,150,25);</span>
<br>

# <span style="color: white;"> rotate(radians(45));</span>
<br>

# <span style="color: white;">rect(25,25,150,25);</span>
<br>




---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Push() & Pop()

## save and load the coordinate systems

::left::
<div>
<img src="/translation_rotate.png" alt="Chart" style="width: 80%" />
</div>

::right::

# <span style="color: white;">push();</span>
<br>

# <span style="color: white;">rotate(radians(45));</span>
<br>

# <span style="color: white;">rect(25,25,150,25);</span>
<br>

# <span style="color: white;">pop();</span>



---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Push() & Pop()

## save and load the coordinate systems

::left::
<div>
<img src="/translation_rotate_from_center.png" alt="Chart" style="width: 80%" />
</div>

::right::

# <span style="color: white;">push();</span>
<br>

# <span style="color: white;">rotate(radians(45));</span>
<br>

# <span style="color: white;">rect(25,25,150,25);</span>
<br>

# <span style="color: white;">pop();</span>
<br>

# <span style="color: red;">rect(25,25,150,25);</span>
<br>

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Exercise

## Using loops and transform

::left::
<div>
<img src="/diamond_pattern_exercise.png" alt="Chart" style="width: 80%" />
</div>

::right::

## <span style="color: white;">Distance from Centre H120px V120px</span>
<br>

## <span style="color: white;">Square Size 200px </span>
<br>

## <span style="color: white;">All rectangles drawn at (0,0) </span>
<br>

## <span style="color: white;">Rotate Group 45 and move to centre </span>
<br>

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Solution (With No Loops)

::left::

```js {*}{lines:true,startLine:1, maxHeight:'410px'}
let centreDist = 120;
let squareSize = 200;

function setup() {
	createCanvas(500, 500);
	background(55, 0, 0);
	angleMode(DEGREES);
	rectMode(CENTER);
}

function draw() {
	translate(width / 2, height / 2);
	rotate(45);
	noFill();
	stroke(125);
	strokeWeight(7);
	rotate(0);

	

```

::right::
```js {*}{lines:true,startLine:1, maxHeight:'430px'}
push();
	translate(-centreDist, -centreDist);
	rect(0, 0, squareSize);
pop();

push();
	translate(centreDist, -centreDist);
	rect(0, 0, squareSize);
pop();

push();
	translate(-centreDist, centreDist);
	rect(0, 0, squareSize);
pop();

push();
	translate(centreDist, centreDist);
	rect(0, 0, squareSize);
pop();
}
```

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
hideInToc: true
---

# Solution (With Loops)

::left::

```js {*}{lines:true,startLine:1, maxHeight:'410px'}
let centreDist = 120;
let squareSize = 200;

function setup() {
	createCanvas(500, 500);
	background(55, 0, 0);
	angleMode(DEGREES);
	rectMode(CENTER);
}

function draw() {
	background(55, 0, 0);
	translate(width / 2, height / 2);
	scale(0.8);
	rotate(frameCount % 360);

	

```

::right::
```js {*}{lines:true,startLine:1, maxHeight:'430px'}
for (let i = 0; i < 4; i++) {
		push();
			noFill();
			stroke(colors[i]);
			strokeWeight(17);
			rotate(i * 90);
				push();
					translate(centreDist, centreDist);
					scale(1.1);
					rect(0, 0, squareSize + sin(frameCount) * 25);
				pop();
		pop();
	}
}
```

