---
title: Make Code More Reusable with the this Keyword
---
# Make Code More Reusable with the this Keyword

---
## Problem Explanation

This challenge is simply demonstrating the power of the `this` keyword. Replacing `dog.numLegs` with `this.numLegs` strengthens our code by directly referencing this object. 
[developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this) has many examples to determine the effects of the `this` keyword.


---
## Solutions

<details><summary>Solution 1 (Click to Show/Hide)</summary>

```javascript
let dog = {
  name: "Spot",
  numLegs: 4,
  sayLegs: function() {
    return "This dog has " + this.numLegs + " legs.";
  }
};

dog.sayLegs();
```

</details>