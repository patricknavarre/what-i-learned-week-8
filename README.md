# `what-i-learned-weeks-7-&-8`



## `Helper Functions`

A `helper function` is a `function` that performs part of the computation of another `function`.   
`Helper functions` are used to make your program easier to read by giving descriptive names to computations.  They also let you reuse computations, just as with `functions` in general.  

Here is an example of a `helper function`.  
````javascript
const isHighPriority = function(todo) {
  return todo.priority === 2
}

const isLowPriority = function(todo) {
  return todo.priority === 1
}
````

The `helper function` then gets used in the following function examples:


````javascript
const priority2Only = function (todos) {
  return todos.filter(isHighPriority)
}

const priority1Only = function (todos) {
  return todos.filter(isLowPriority)
}


````



----------
## `Helper Methods` 

## `.map`

* The `.map` helper iterates over an `array`, running the callback `function` on each element as it iterates through the `array`. 

* `.map`  will return a new `array` where the value of each element is the returned value of the callback `function` that was provided to the `.map` helper.  

* `.map` is used when you want to perform data manipulation without mutating the original data set.  

* `.map` ALWAYS pushes in to the new `array` once for every element of the old `array`.

* `.map` ALWAYS runs each element through a transformation function before pushing it.  

The `.map` helper below returns a new `array` that contains the square of each value in the numbers `array`.  

````javascript
const numbers = [1, 2, 3, 4, 5];

// using a for loop
const squared = [];
   for (let i = 0; i < numbers.length; i++){
       squared.push(numbers[i] * numbers[i])
   }

console.log(squared) // [1, 4, 9, 16, 25]

// using .map
const squared = numbers.map(number => number * number);
console.log(squared) // [1, 4, 9, 16, 25]
````
---------

## `.filter`

The `.filter` helper iterates over the array and returns a new array that will contain the values that are returned `true` when passed through the callback `function`.

Here's an example of a `.filter` helper returning an `array` containing all of the even values from inside the numbers `array`.

```javascript
const numbers = [1, 2, 3, 4, 5, 13, 14, 21, 20];
// using a for loop
const filtered = [];

for (let i = 0; i < numbers.length; i++){
    if (numbers[i] % 2 === 0){
        filtered.push(numbers[i])
    }
}
console.log(filtered); // [2, 4, 14, 20]

// using .filter
const filtered = numbers.filter(number => {
    if (number % 2 === 0){
        return true;
    }
});

console.log(filtered); // [2, 4, 14, 20]
```

## `.reduce`

To oversimplify the `reduce` function, you can use the `.reduce` helper to transform an `array` of values into a single value. Some would say that the `.reduce` helper can be used to get the essence of a set of data. In the following example you will see how `.reduce` will sum up the values in the **`numbers`** `array`.

````javascript
const numbers = [1, 2, 3, 4, 5];

// using a for loop
let sum = 0;

for (let i = 0; i < numbers.length; i++){
    sum += numbers[i];
}

console.log(sum) // 15

// reduce helper
numbers.reduce((sum, number) => sum + number, 0): // 15
````

So, the `reduce` helper is executing the callback `function` on each iteration and produces a single result at the end.  In the example above that value is `sum`.  

The `reduce` helper method can take in 5 arguments.  

1. `accumulator`
2. `currentValue`
3. `currentIndex`
4. `array`
5. `initialValue`

The `accumulator` and `currentValue` are required, while the other three arguments are optional.  On each iteration the `reduce` helper first checks to see if an initial value has been passed in, then the `accumulators` value is set to equal the inital value.  If no inital value has been passed in, then the `accumulator` will be set to the value of the element in the provided array.  

If the initial value argument has been passed in, then the `function` will set the `accumulator` **`sum`** to be equal to the initial value.  I pass in an initial value so the **`sum`** will be set to 0 on the first iteration.  The `currentIndex` or `number` is set to the next value in the `array`.  At the beginning of the `reduce` helper `function`, that will be 1 or the first value inside the **`numbers`** `array`.  

 I added a `console.log` to the **`reduce`** `function` to show the value of **`sum`** on each iteration. 

```javascript
const numbers = [1, 2, 3, 4, 5]
numbers.reduce( (sum, number) => return sum + number, 0);
// Iteration 1: sum = 0, number = 1; return sum = 1;
// Iteration 2: sum = 1, number = 2; return sum = 3;
// Iteration 3: sum = 3, number = 3; return sum = 6;
// Iteration 4: sum = 6, number = 4; return sum = 10;
// Iteration 5: sum = 10, number = 5; return sum = 15;
```







