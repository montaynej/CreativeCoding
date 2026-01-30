---
layout: two-cols
layoutClass: gap-x-6 gap-y-2 p-10
---

# Mapping

## Converting one range of values into another.


### map()

```js {*|3|*}{lines:true,startLine:1}
var a = map(mouseX, 0, 600, 0, 360);
rotate(radians(a));
rect(300, 300, 50, 50);
```

- First Parameter = The Value requiring to be mapped

- Input Range (Next Pair of Parameters) = Minimum and maximum of source range

- Output Range (Next Pair) = Minimum and maximum of target range

::right::
<div>
<img src="https://github.com/montaynej/Images-for-Slides/blob/main/Screenshot%202026-01-16%20at%2021.07.53.png?raw=true" alt="Chart" style="width: 70%" />
</div>

<br>

<div>
<img src="https://github.com/montaynej/Images-for-Slides/blob/main/Screenshot%202026-01-16%20at%2021.08.04.png?raw=true" alt="Chart" style="width: 70%" />
</div>

<br>
<div>
<img src="https://github.com/montaynej/Images-for-Slides/blob/main/Screenshot%202026-01-16%20at%2021.08.14.png?raw=true" alt="Chart" style="width: 70%" />
</div>

