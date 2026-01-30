---
layout: image-right
image: https://images.unsplash.com/photo-1754820978711-611479056f97?q=80&w=1674&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
---

# Interactivity

## Mouse and keyboard input.

### Mouse

```js {*|3|*}{lines:true,startLine:1}
mouseX
mouseY
```

```js {*|3|*}{lines:true,startLine:1}
function draw() {
  rect(mouseX, mouseY, 50, 50);
}
```

### Mouse Pressed

```js {*|3|*}{lines:true,startLine:1}
function draw() {
  if (mouseIsPressed) {
    rect(mouseX, mouseY, 50, 50);
  }
}
```

---
layout: image-right
image: https://images.unsplash.com/photo-1529236183275-4fdcf2bc987e?q=80&w=1767&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
---

# Interactivity

## Mouse and keyboard input.

```js {*|3|*}{lines:true,startLine:1}
keyIsPressed
key
```

```js {*|3|*}{lines:true,startLine:1}
function draw() {
  if (keyIsPressed && key == 'r') {
    rect(mouseX, mouseY, 50, 50);
  }
}
```
