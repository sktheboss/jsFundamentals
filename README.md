1. **Array Manipulation:**

   a) Write a function that flattens a nested array. For example, given `[1, [2, [3]], 4]`, return `[1, 2, 3, 4]`.

   b) Implement a function that finds the unique elements in an array.

   c) Create a function that groups the elements of an array based on a given function. For example, given an array of numbers, group the even and odd numbers.

2. **String Manipulation:**

   a) Write a function that reverses a string without using built-in `reverse` method.

   b) Implement a function that counts the occurrences of each character in a string.

   c) Create a function that capitalizes the first letter of each word in a sentence.

3. **Object Manipulation:**

   a) Write a function that deep clones an object.

   b) Implement a function that merges two objects, where the second object's properties override the first object's properties.

   c) Create a function that checks if two objects are equal (deep equality).

4. **Async/Await and Promises:**

   a) Write a function that simulates asynchronous behavior using `setTimeout` and returns a resolved or rejected promise.

   b) Implement a function that executes multiple asynchronous functions in parallel and returns their results.

   c) Create a function that fetches data from a remote API using `fetch` and handles errors using promises.

5. **Functional Programming:**

   a) Write a higher-order function that takes a function and returns a new function that can only be called once.

   b) Implement a currying function that allows a function to be partially applied.

   c) Create a function that composes multiple functions into a single function.

6. **Algorithms and Data Structures:**

   a) Write a function to find the nth Fibonacci number using recursion.

   b) Implement a function that sorts an array using a common sorting algorithm (e.g., quicksort, mergesort).

   c) Create a data structure (e.g., stack, queue, linked list) and implement its basic operations.
```
/**
 * A utility class for Arrays.
 * @class
 * @description Provides a variaous range of array functions which will help to do operations on Arrays.
 * @author Suraj Kumar <suraj.1001kumar@gmail.com>
 */
class ArrayHelper {
  /**
   *
   * @param {Array} arr Nested array
   * @return {Array} Flatten Array
   * @author Suraj Kumar <suraj.1001kumar@gmail.com>
   * @description This methods flatten a multidimensional array. For example, given `[1, [2, [3, 4]], 5]`, return `[1, 2, 3, 4]`.
   * If already a flatten array is given it will return the same array. If the Input array is not an array then it will return an empty array.
   */
  static flat(arr) {
    if (!arr || arr.length === 0 || !Array.isArray(arr)) {
      console.log("Error");
      return;
    }

    return arr.reduce((flattenArray, elem) => {
      if (Array.isArray(elem)) {
        return [...flattenArray, ...ArrayHelper.flat(elem)];
      } else {
        return [...flattenArray, elem];
      }
    }, []);
  }

  static uniqueValues(arr, condition = 0){
    if (!arr || arr.length === 0 || !Array.isArray(arr)) {
        console.log("Error");
        return [];
    }
    switch(condition){
        case condition == 1:
            return arr.filter((item, index) => arr.indexOf(item) === index)
        case condition == 2:
            return arr.reduce((unique, item) => {
                if (!unique.includes(item)) {
                  unique.push(item);
                }
                return unique;
              }, []);
        case condition == 0:
        default:
            return new Array(...new Set(arr));
    }
    

  }
}

console.log(ArrayHelper.flat([1, [2, [3, [2, 3, 4, 5, [5, 55, 1]]]], 5]));
console.log(ArrayHelper.uniqueValues([1,2,2,3,4,4,5,5,4,5,43,2,1], 0))
console.log(ArrayHelper.uniqueValues([1,2,2,3,4,4,5,5,4,5,43,2,1], 1))
console.log(ArrayHelper.uniqueValues([1,2,2,3,4,4,5,5,4,5,43,2,1], 2))
```
