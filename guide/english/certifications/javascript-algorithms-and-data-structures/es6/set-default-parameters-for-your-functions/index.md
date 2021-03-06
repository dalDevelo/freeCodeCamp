---
title: Set Default Parameters for Your Functions
---

# Set Default Parameters for Your Functions

---
## Problem Explanation

We'll be modifying the increment function so that the **number** parameter is incremented by 1 by default, by setting **value** to 1 if a value for **value** is not passed to the increment function.


---
## Hints

### Hint 1

Let's identify where the parameter **value** is in JS function

try to solve the problem now

### Hint 2

Set **value** equal to something so that it is that value by default

try to solve the problem now



---
## Solutions

<details><summary>Solution 1 (Click to Show/Hide)</summary>

```javascript
const increment = (function() {
  "use strict";
  return function increment(number, value = 1) {
    return number + value;
  };
})();
console.log(increment(5, 2)); // returns 7
console.log(increment(5)); // returns NaN
```

#### Code Explanation

* This section is pretty straightforward. Pass this section by setting the **value** parameter equal to 1. When the function comes across test cases where **value** has not been passed anything, then **value** will be assigned one by default.

Relevant Links:

[JavaScript default parameters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters)

* DO NOT add solutions that are similar to any existing solutions. If you think it is similar but better, then try to merge (or replace) the existing similar solution.
* Categorize the solution in one of the following categories — Basic, Intermediate and Advanced.
</details>
