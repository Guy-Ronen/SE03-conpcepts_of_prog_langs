# Higher order functions

Higher-order functions are functions that take other functions as arguments or return functions as their results. They are a key concept in functional programming, and they enable powerful and concise ways of abstracting over code.

## Higher-order functions characteristics
Higher-order functions have a few key characteristics:

1. They take one or more functions as arguments. This is what distinguishes higher-order functions from regular functions.
<br>
2. They return functions as results. This allows higher-order functions to be used to construct new functions based on existing ones.
<br>
3. They can be used to abstract over common patterns and operations. Higher-order functions allow you to write more reusable and composable code by extracting patterns into functions that can be reused throughout your codebase.
<br>
4. They can be used to implement advanced programming techniques, such as closures, currying, and partial application. These techniques allow you to create more flexible and powerful functions that can be customized and combined in a variety of ways.

### Three common higher-order functions:
1. `map()`: The map function takes a function as an argument and applies it to each element in the collection. It then returns a new collection containing the result of applying the function to each element in the original collection.

#### map() example:

```javascript
function map(func, arr) {
  const result = []
  for (let i = 0; i < arr.length; i++) {
    result.push(func(arr[i]))
  }
  return result
}

function square(x) {
  return x ** 2
}

const nums = [1, 2, 3, 4, 5]
const squared = map(square, nums)
console.log(squared) // prints [1, 4, 9, 16, 25]
```
<br>

2. `filter()`: The filter function takes a predicate function as an argument and returns a new collection containing only the elements that satisfy the predicate.

#### filter() example:

```javascript
function filter(condition, arr) {
  const result = []
  for (let i = 0; i < arr.length; i++) {
    if (condition(arr[i])) {
      result.push(arr[i])
    }
  }
  return result
}

function isEven(x) {
  return x % 2 === 0
}

const nums = [1, 2, 3, 4, 5]
const evens = filter(isEven, nums)
console.log(evens) // prints [2, 4]
```
<br>

3. `reduce()`: The reduce function takes a binary operator function as an argument and applies it to all elements in the collection to produce a single value.


#### reduce() example:
```javascript
function reduce(func, arr, initial) {
  let result = initial
  for (let i = 0; i < arr.length; i++) {
    result = func(result, arr[i])
  }
  return result
}

function add(x, y) {
  return x + y
}

const nums = [1, 2, 3, 4, 5]

const sumZero = reduce(add, nums, 0)
console.log(sumZero) // prints 15

const sumOne = reduce(add, nums, 1)
console.log(sumOne) // prints 16
```