### Searching Algorithms

#### 1. Linear Search:

Linear search is a simple searching algorithm that sequentially checks each element in a list or array until a match is found or the entire list has been searched. It is also known as sequential search.

Linear search has a time complexity of **O(n)**.

Input / Output:

Input: An array of elements and a target value to search for.
Output: The index of the target value in the array if found, otherwise -1.

Explanation:

- Start at the beginning of the array.
- Iterate through each element of the array sequentially.
- Compare each element with the target value.
- If a match is found, return the index of that element.
- If the entire array is traversed and no match is found, return -1.

```javascript
function linearSearch(arr, target) {
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === target) {
      return i; // Element found, return its index
    }
  }
  return -1; // Element not found in the array
}

// Example usage:
const array = [5, 3, 8, 1, 4, 9];
const targetValue = 8;
const resultIndex = linearSearch(array, targetValue);

if (resultIndex !== -1) {
  console.log(`Element ${targetValue} found at index ${resultIndex}.`);
} else {
  console.log(`Element ${targetValue} not found in the array.`);
}
```

#### 1. Linear Search:

Linear search is a simple searching algorithm that sequentially checks each element in a list or array until a match is found or the entire list has been searched. It is also known as sequential search.

Linear search has a time complexity of **O(n)**.

```javascript
function linearSearch(arr, target) {
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === target) {
      return i; // Element found, return its index
    }
  }
  return -1; // Element not found in the array
}

// Example usage:
const array = [5, 3, 8, 1, 4, 9];
const targetValue = 8;
const resultIndex = linearSearch(array, targetValue);

if (resultIndex !== -1) {
  console.log(`Element ${targetValue} found at index ${resultIndex}.`);
} else {
  console.log(`Element ${targetValue} not found in the array.`);
}
```
