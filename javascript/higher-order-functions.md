# JavaScript Higher-Order Functions

## Video: Higher-Order Functions
[![YouTube](http://img.youtube.com/vi/nIDcPIr94bk/0.jpg)](https://www.youtube.com/watch?v=nIDcPIr94bk)

## Overview
- Higher-order functions are functions that take in another function as an argument OR returns a function as an output

## Learning Objectives
- Understanding the anatomy of a higher-order function
- Understanding the use of .map()
- Understanding the use of .filter()
- Understanding the specific parameters available to higher order functions

## Vocabulary
- higher-order function
- value, index

## Set Up
- Create a file in a text editor with the extension `.js`
- In terminal, `cd` into the appropriate folder
- $ `node filename.js`

## Higher-Order Functions
A higher-order function is simply a function that either takes in another function as an argument or returns another function as an output.

We will focus on two higher-order functions for this lesson - **.map()** and **.filter()** both have three built-in parameters - the value, index, and array.

What the parameters are named is arbitrary, but the order will always be the same. The higher-order functions have to take at least one argument (value) but can take two or three if needed.

* .map(value, index, array)
* .filter(value, index, array)


1. The **value** at each index of an array

2. The **index** of the array that we are iterating through (Optional)  

3. The **array** that higher-order function was called on. (Optional)


## .map()

The **.map()** function iterates through an array and returns a new array of the same length.

Here is an example of iterating using a for loop:

```javascript
var myArray = [5, 3, 2, 9, 8];

let newArray = [];
for(let i=0; i<arr.length; i++){
  let valueTimesThree = myArray[i] * 3;
  console.log(valueTimesThree);
  newArray.push(valueTimesThree);
}

console.log(newArray);
```

Now let's look at this same objective with **.map()**

```javascript
var myArray = [5, 3, 2, 9, 8]

const multiplier = myArray.map(value => {
    return value * 3
})

console.log(multiplier)
```

Because we are using an arrow function we can reduce the code even further. If there is only one line of code to be executed, we can remove the `return` keyword as the return is implied.

```javascript
var myArray = [5, 3, 2, 9, 8]

const multiplier = myArray.map(value => value * 3)

console.log(multiplier)
```

And finally let's wrap the .map() logic in a function that can take in any array to make the function reusable.

```javascript
var myArray = [5, 3, 2, 9, 8]

const multiplier = (array) => {
  return array.map(value => value * 3)
}
console.log(multiplier(myArray))
```

Notice that .map() *iterates* through the specified array **AND** returns a new array with the updated values.

Here is another example with proper pseudocoding:
```javascript
// create a function that takes in an array and returns each word capitalized
var fruitArray = ["banana", "mango", "apple", "grape"]

// declare a function that takes in an array
const capitalizer = (array) => {
  // create a local variable that maps through the array
  let eachItem = array.map(value => {
    // with each value access the first index and capitalize the letter then concatenate the remainder of the word
    return value[0].toUpperCase() + value.substring(1)
  })
  // return the local variable joined into a string
  return eachItem.join(" ")
}
// logging the function and pass in the array
console.log(capitalizer(fruitArray))
```
**Note:** - This function has a return for the outer function **AND** a return for the higher-order function.

---

## .filter()

The **.filter()** function loops through an array and returns a new array with only the values that are **truthy** or the values that satisfy your stated condition. Filter will return a subset of the given array.

Here is an example of *iterating* and returning a subset using a for loop:

```javascript
var numbersArray1 = [1, 2, 7, 4, 10, 8, 9]

const onlyEven = (array) => {
  let newArr = []
  for(let i=0; i<array.length; i++){
    if(array[i] % 2 === 0){
      newArr.push(array[i])
    }
  }
  return newArr
}

console.log(onlyEven(numbersArray1))
```

So, in the above example, we have created a function that takes an array as an argument, loops through the array, and returns a new array containing only the even numbers.

#### **Using .filter()**

```javascript
var numbersArray1 = [1, 2, 7, 4, 10, 8, 9]

const onlyEven = (array) => {
  return array.filter(value => value % 2 === 0)
}

console.log(onlyEven(numbersArray1))
```

Here is another example with proper pseudocoding:
```javascript
// create a function that returns only the values at the odd indexes
var numbers = [4, 24, 5, 9, 0, 78]

// declare a function that takes in an array
const getOnlyOddIndex = (array) => {
  // return a higher-order function that takes in the value and the index
  return array.filter((value, index) => {
    // return only the values that have an odd index
    return index % 2 !== 0
  })
}
// log the function and pass in the array
console.log(getOnlyOddIndex(numbers))
```


## .map() vs .filter()

When deciding which higher-order function to use, remember these two differences:

- **.map()** will do something to each item in an array and _return the same number of items_.
- **.filter()** will return a new, likely smaller array _filtered_ based on your specified criteria.

---
## Challenges

> **DON'T FORGET TO PSEUDO CODE!**

> ***Use .map() or .filter() to complete all of the following exercises:***

- 1. **Write a function that takes in an array and returns a new array with all numbers multiplied by 10.**

  ```javascript 
  var arr1 = [3, 9, 15, 4, 10]
  ```

  Expected output: 
  ```javascript 
  [30, 90, 150, 40, 100]
  ```
  ---

- 2. **Write a function that takes in an array and returns a new array with only odd numbers**

  ```javascript 
  var arr2 = [2, 7, 3, 5, 8, 10, 13]
  ```

  Expected output: 
  ```javascript 
  [7, 3, 5, 13]
  ```

  ---

- 3. Write a function that takes in an array of numbers and letters and returns a string with only the letters. **HINT:** Use *[typeof](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof)* method

  ```javascript 
  var comboArr = [7, "n", "i", "c", 10, "e", false, "w", 3, "o", "r", "k"]
  ```

  Expected output: 
  ```javascript 
  "nicework"
  ```

  ---

### STRETCH Challenges

- 1. Create a function that takes in a string and returns a new string with all the vowels removed.

  ```javascript
   var str = "javascript is awesome" 
   ```

  Expected output:
  ```javascript
  "jvscrpt s wsm"
  ```

---
- 2. Create a function that takes in two arrays as arguments returns one array with no duplicate values.

  ```javascript
  var arr1 = [3, 7, 10, 5, 4, 3]

  var arr2 = [7, 8, 2, 1, 5, 4]
  ```

  Expected output:
  
  ```javascript 
  [3, 7, 10, 5, 4, 8, 2, 1]
  ```

  ---

[ Go to next lesson: JavaScript Testing with Jest ](./jest.md)

[ Back to JavaScript Functions, Loops, and Arrays ](./functions-loops-arrays.md)

[ Back to Syllabus ](../README.md#unit-one-javascript-foundations)
