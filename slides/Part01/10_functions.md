---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Defining Functions
## needs to know

::left::

### Declaring a function
```js {*|3|*}{lines:true,startLine:1}
function doSomething() {
  console.log("I Just clapped")
}

doSomething();
doSomething();
```

### Functions Expression

```js {*|3|*}{lines:true,startLine:1}
let addTwoThings = (a,b) => a+b;
// let addTwoThings = function(a,b){ 
  //return a+b;
 // }

addTwoThings(23,34)
```

::right::
### Function with Parameter

```js {*|3|*}{lines:true,startLine:1}
function doSomething(numTimes) {
  for(let i=0; i<numTimes; i++){
    console.log("clap)
  }
  console.log('I just clapped ${numTimes} times')
}
doSomethinng(3);

```


### Returning Values

```js {*|3|*}{lines:true,startLine:1}
function average(a, b) {
  return (a + b) / 2;
}

var result = average(40, 30);
```

