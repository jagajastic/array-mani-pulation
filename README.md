# Array Manipulation 

### How to Use Array Destructuring

General way

```
const fruits = ["🍎", "🍌", "🍒"];

const apple = fruits[0];
console.log(apple); // "🍎"

const banana = fruits[1];
console.log(banana); // "🍌"

const cherry = fruits[2];
console.log(cherry); // "🍒"
```

Better approach

```
const [apple, banana, cherry] = ["🍎", "🍌", "🍒"];

console.log(apple); // "🍎"
console.log(banana); // "🍌"
console.log(cherry); // "🍒"

```

Tricky way(skipping one item) 

```
const [apple, , cherry] = ["🍎", "🍌", "🍒"];

console.log(apple); // "🍎"
console.log(cherry); // "🍒"
```

Assigning a default value

```
// Assign a default value for a missing element.
const [apple, banana, cherry, melon = "🍉"] = ["🍎", "🍌", "🍒"];
console.log(melon); // "🍉"

// Get all remaining elements from an array using the spread operator (`...`).
const [apple, ...remainingFruits] = ["🍎", "🍌", "🍒"];
console.log(remainingFruits); // ["🍌", "🍒"]
```

### How to Create a Duplicate-free Version of an Array

```
const fruits = ["🍎", "🍌", "🍌", "🍒", "🍎"];

// Create a new set from `fruits`, thereby removing all duplicates.
// Then, create a new array from it.
const uniqueFruits = [...new Set(fruits)];

console.log(uniqueFruits); // ["🍎", "🍌", "🍒"]
```

### How to Find All Elements Matching a Condition

```
const names = ["Kai", "Katharina", "Tim"];

// Keep names that are shorter than 4 characters.
const short Names = names.filter(name => name.length < 4);
console.log(shortNames); // ["Kai", "Tim"]

// Find names that are longer than 10 characters.
const extraLongNames = names.filter(name => name.length > 10);
console.log(extraLongNames); // []
```


### How to Remove All Falsy Values From an Array


```
const fruits = ["🍎", false, "🍌", undefined, "🍒"];

// Keep all array elements where `fruit` is truthy.
const filteredFruits = fruits.filter(fruit => fruit);

console.log(filteredFruits); // ["🍎", "🍌", "🍒"]
```


### How to Find the First Element Matching a Condition


```
const names = ["Kai", "Katharina", "Tim"];

// Find a name that is shorter than 4 characters.
const shortName = names.find(name => name.length < 4);
console.log(shortName); // "Kai"

// Find a name that is longer than 10 characters.
const extraLongName = names.find(name => name.length > 10);
console.log(extraLongName); // undefined
```


### How to Check If Any / Every Element Matches a Condition

```
const names = ["Kai", "Katharina", "Tim"];

// Check if ANY name is shorter than 4 characters.
const containsShortName = names.some(name => name.length < 4);
console.log(containsShortName); // true

// Check if EVERY name is longer than 3 characters.
const containsLongNamesOnly = names.every(name => name.length > 3);
console.log(containsLongNamesOnly); // false
```

### How to Find the Intersection of Two Arrays

```
const fruitsA = ["🍎", "🍌", "🍒"];
const fruitsB = ["🍒", "🍆", "🍉", "🍌"];

const intersection = fruitsA.filter(fruit => fruitsB.includes(fruit));
console.log(intersection); // ["🍌", "🍒"]
```


### How to Find the Difference of Two Arrays

```
const fruitsA = ["🍎", "🍌", "🍒"];
const fruitsB = ["🍒", "🍆", "🍉", "🍌"];

// Keep all elements from `fruitsA` that are not included in `fruitsB`. 
const difference = fruitsA.filter(fruit => !fruitsB.includes(fruit));
console.log(difference); // ["🍎"]

// Keep all elements from `fruitsA` that are not included in `fruitsB` and vice versa.
const difference = [
  ...fruitsA.filter(fruit => !fruitsB.includes(fruit)),
  ...fruitsB.filter(fruit => !fruitsA.includes(fruit)),
];
console.log(difference); // ["🍎", "🍆", "🍉"]
```

### How to Find the Union of Two Arrays


```
const fruitsA = ["🍎", "🍌", "🍒"];
const fruitsB = ["🍒", "🍆", "🍉", "🍌"];

// Merge `fruitsA` and `fruitsB`. Then, use a set for removing duplicates.
// After that, create a new array from the set.
const union = [...new Set([...fruitsA, ...fruitsB])];
console.log(union); // ["🍎", "🍌", "🍒", "🍆", "🍉"]
```

### How to Retrieve the First and Last Element

```
const fruits = ["🍎", "🍌", "🍒"];

// Find the first element. Attention! This modifies the original array.
const first = fruits.shift();
console.log(first); // "🍎"

// Find the last element. Attention! This modifies the original array.
const last = fruits.pop();
console.log(last); // "🍒"

// Remember, both methods modify the original array.
console.log(fruits); // ["🍌"]
```

### How to Prepend / Append an Element to an Array

```
const fruits = ["🍎", "🍌", "🍒"];

// Append an element with `Array#push`.
// This means, we'll add it to the end.
fruits.push("🍉");
console.log(fruits); // ["🍎", "🍌", "🍒", "🍉"];

// Prepend an element with `Array#unshift`.
// This means, we'll add it to the beginning.
fruits.unshift("🍆");
console.log(fruits); // ["🍆", "🍎", "🍌", "🍒", "🍉"];

// You can also add multiple items at once.
// Works with `push` and `unshift`.
fruits.push("🍍", "🍊");
fruits.unshift("🍍", "🍊");

// Also, you could use the spread operator (...).
// This would add all elements from another array.
fruits.push(...["🍍", "🍊"]);
fruits.unshift(...["🍍", "🍊"]);
```

### How to Copy an Array

```
// This example is similar to tip 11.
const fruitsA = ["🍎", "🍌", "🍒"];

// Here, we copy the `fruitsA` array.
const fruitsB = fruitsA.slice();

// Find the first element. Attention! This modifies our `fruitsB` array.
const first = fruitsB.shift();
console.log(first); // "🍎"

// Find the last element. Attention! This modifies our `fruitsB` array.
const last = fruitsB.pop();
console.log(last); // "🍒"

// This time, our original arrays stays intact.
// Only `fruitsB` has changed.
console.log(fruitsA); // ["🍎", "🍌", "🍒"]
console.log(fruitsB); // ["🍌"]
```

### How to Find the Minimum and Maximum Value From an Array

```
const priceHistory = [450, 500, 330, 600, 910];

// Find the minimum value.
const minimumPrice = Math.min(...priceHistory);
console.log(minimumPrice); // 330

// Find the maximum value.
const maximumPrice = Math.max(...priceHistory);
console.log(maximumPrice); // 910
```

### How to Sort an Array of Numbers

```
const numbers = [15, 52, 23, 11, 9];

// Sort in ascending order. Attention! This modifies the original array.
numbers.sort((a, b) => a - b);
console.log(numbers); // [9, 11, 15, 23, 52]

// Sort in descending order. Attention! Again, this modifies the original array.
numbers.sort((a, b) => b - a);
console.log(numbers); // [52, 23, 15, 11, 9]
```
