---
title: Delete Properties from a JavaScript Object
---
# Delete Properties from a JavaScript Object

### Hint 1 
* change the properties of myDog by using dot notation


---
## Solutions

<details><summary>Solution 1 (Click to Show/Hide)</summary>

```javascript
var ourDog = {
  name: "Camper",
  legs: 4,
  tails: 1,
  friends: ["everything!"],
  bark: "bow-wow"
};

delete ourDog.bark;

// Setup
var myDog = {
  name: "Happy Coder",
  legs: 4,
  tails: 1,
  friends: ["freeCodeCamp Campers"],
  bark: "woof"
};

// Only change code below this line.
delete myDog.tails;
```
</details>

