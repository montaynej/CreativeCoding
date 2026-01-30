---
layout: image-right
image: https://images.unsplash.com/photo-1649838514794-beed50cf67a3?q=80&w=1773&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
---

# Animation

## A movie is a sequence of frames.


### setup() and draw()

```js {*|3|*}{lines:true,startLine:1}
let xPos=0

function setup() {
  size(500, 500);
}

function draw() {
	background(125)
	fill(0)
	ellipse(0, 0, xPos, 50);
	xPos++
}
```

### Important
Setup() is called once in the sketch while Draw() is called every frame

