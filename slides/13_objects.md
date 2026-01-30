---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Introducting Objects
## Encapsulation - wrapping data and behavior within a single entity

::left::

<div style="font-size: 248px; margin-top:0px; color: orange;">{}</div>

::right::

```js {*}{lines:true,startLine:1, maxHeight:'380px'}
let friend01 = { name: "David", age: 24, bowling: true };
console.log(friend01.age);

if(friend01.bowling){ 
	console.log('Friend01 likes bowling')
}

let friend02 = { name: "Peter", age: 29, bowling: false };
let friend03 = { name: "Mary", age: 34, bowling: true };

let friends = [];
friends.push(friends01)
friends.push(friends02)
friends.push(friends03)

console.log (friends[1].age)

```

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Using useful Array methods
## The filter() and map() methods

::left::

```js {*}{lines:true,startLine:1, maxHeight:'380px'}
let friends =
[
    {
        "name": "David",
        "age": 24,
        "bowling": true
    },
    {
        "name": "Mary",
        "age": 34,
        "bowling": false
    },
    {
        "name": "Paul",
        "age": 21,
        "bowling": true
    }
]
```

::right::

### Using the map()


```js {*}{lines:true,startLine:1, maxHeight:'380px'}
let friendsAges = friends.map(friend => friend.age)
```
This creates a new array and maps all of the ages into that new array

```js {*}{lines:true,startLine:1, maxHeight:'380px'}
console.log(friendsAges)

[24,34,21]
```

---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Using useful Array methods
## The filter() and map() methods

::left::

```js {*}{lines:true,startLine:1, maxHeight:'440px'}
let friends =
[
    {
        "name": "David",
        "age": 24,
        "bowling": true
    },
    {
        "name": "Mary",
        "age": 34,
        "bowling": false
    },
    {
        "name": "Paul",
        "age": 21,
        "bowling": true
    }
]
```

::right::

### Using the filter()


```js {*}{lines:true,startLine:1, maxHeight:'380px'}
let bowlingFriends = friends.filter(friend => friend.bowling == true)
```

### This creates a new array and similar to the starting array of objects but with only the bowling friends we can than map this

```js {*}{lines:true,startLine:1, maxHeight:'380px'}
let bowlingFriendAges = bowlingFriends.map(friend => friend.age)
console.log(bowlingFriendAges)
[24,21]
```

### This could be done in one line

```js {*}{lines:true,startLine:1, maxHeight:'380px'}
let bowlingFriendsAges = friends
    .filter(friend => friend.bowling == true)
    .map(friend => friend.age);
console.log(bowlingFriendAges)
[24,21]
```


---
layout: two-cols-header
layoutClass: gap-x-6 gap-y-2 p-10
---

# Importing CSV Data
## Will create an array of objects

::left::

```js {*}{lines:true,startLine:1, maxHeight:'440px'}

let cleanData
function preload() {
	data = loadTable("data/friends.csv", "csv", "header");
}

function setup() {

    for (let i = 0; i < data.rows.length; i++) {
		cleanData.push(data.rows[i].obj);
	}
	createCanvas(500, 500);
}
```
This creates an array of 100 objects. Some who like Bowling and some who do not. 

::right::

# Exercise !

- Your task is to filter out the people who do not like bowling and then map their ages into a new Array.

- Write a function that will accept and array as a parameter and by looping through the array is able to calculate the average of your bowling friends

