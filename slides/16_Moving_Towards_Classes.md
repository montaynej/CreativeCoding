---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Moving Towards Classes & Objects 

## A simple example

::left::
Lets go back to our Friend Object
```js {wrap:true}
{name: "David", age:23, bowling:true}
```
So all of our friends will have the same structure but different content

<br>

> So let's Define that structure in a class

```js 
class Friend {
	constructor(){
		this.name= "David";
		this.age = 23;
		this.bowling = true;
	}
}
```


::right::

Now when we want an instance of our class (an object)
```js
let test = new Friend();
console.log(test)

-- output {name:"David", age:23, bowling:true}
```

But we dont want every object to be the same. We need to be able to pass it some parameters


---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Moving Towards Classes & Objects

## A simple example

::left::

> Our new Class structure

```js 
class Friend {
	constructor(_name, _age, _bowling){
		this.name= _name;
		this.age = _age;
		this.bowling = _bowling;
	}
}
```

```js
let test = new Friend("John",32, false);
```

```js
console.log(test)
-- output {name:"John", age:32, bowling:false}

```

Every friend can now be unique and not the same

::right::

> Lets Add a Method

```js {wrap:true}
class Friend {
	constructor(_name, _age, _bowling){
		this.name= _name;
		this.age = _age;
		this.bowling = _bowling;
	}

	this.report(){
		console.log(`${this.name} is ${this.age} years of age.`)
	}
}
```

And use test.report() to view output in console
