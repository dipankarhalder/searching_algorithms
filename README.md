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

#### 2. Binary search:

Binary search is a more efficient searching algorithm compared to linear search, especially for sorted arrays. It works by repeatedly dividing the search interval in half.

Binary search has a time complexity of **O(log n)**.

Input / Output:

Input: A sorted array and a target value to search for.
Output: The index of the target value in the array if found, otherwise -1.

Explanation:

- Start with the entire array.
- Find the middle element of the array.
- Compare the middle element with the target value.
  - If the middle element is equal to the target value, return its index.
  - If the middle element is greater than the target value, search the left half of the array.
  - If the middle element is less than the target value, search the right half of the array.
- Repeat steps 2 and 3 until the target value is found or the search interval becomes empty.
- If the target value is not found after the entire array is searched, return -1.

```javascript
function binarySearch(arr, target) {
  let left = 0;
  let right = arr.length - 1;

  while (left <= right) {
    let mid = Math.floor((left + right) / 2);

    // Check if target is present at mid
    if (arr[mid] === target) {
      return mid;
    }

    // If target is greater, ignore left half
    if (arr[mid] < target) {
      left = mid + 1;
    } else {
      // If target is smaller, ignore right half
      right = mid - 1;
    }
  }

  // Element not found in the array
  return -1;
}

// Example usage:
const sortedArray = [1, 3, 4, 5, 8, 9];
const targetValue = 8;
const resultIndex = binarySearch(sortedArray, targetValue);

if (resultIndex !== -1) {
  console.log(`Element ${targetValue} found at index ${resultIndex}.`);
} else {
  console.log(`Element ${targetValue} not found in the array.`);
}
```
