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

#### 3. Depth-First Search (DFS):

Depth-First Search (DFS) is a traversal algorithm used to explore nodes of a graph or tree data structure. It starts at a selected node and explores as far as possible along each branch before backtracking.

DFS can be implemented using either a recursive or iterative approach. The recursive approach is more straightforward and elegant, while the iterative approach typically uses a stack data structure to keep track of nodes to visit.

Input / Output:

Input: A graph or tree data structure and a starting node.
Output: The nodes visited in the order they were explored.

Explanation:

- Start at the selected node and mark it as visited.
- Explore the unvisited adjacent nodes recursively or iteratively.
- Repeat step 2 for each unvisited adjacent node.
- Backtrack if no unvisited adjacent nodes are left.

```javascript
class Graph {
  constructor() {
    this.adjacencyList = {};
  }

  // Add a vertex to the graph
  addVertex(vertex) {
    if (!this.adjacencyList[vertex]) {
      this.adjacencyList[vertex] = [];
    }
  }

  // Add an edge between two vertices
  addEdge(vertex1, vertex2) {
    this.adjacencyList[vertex1].push(vertex2);
    this.adjacencyList[vertex2].push(vertex1); // For undirected graph
  }

  // Depth-First Search
  dfsRecursive(start) {
    const visited = {};
    const result = [];

    const dfs = (vertex) => {
      if (!vertex) return;

      visited[vertex] = true;
      result.push(vertex);

      this.adjacencyList[vertex].forEach((neighbor) => {
        if (!visited[neighbor]) {
          dfs(neighbor);
        }
      });
    };

    dfs(start);
    return result;
  }
}

// Example usage:
const graph = new Graph();
graph.addVertex("A");
graph.addVertex("B");
graph.addVertex("C");
graph.addVertex("D");
graph.addVertex("E");
graph.addEdge("A", "B");
graph.addEdge("A", "C");
graph.addEdge("B", "D");
graph.addEdge("C", "E");

console.log(graph.dfsRecursive("A"));
```

#### 4. Breadth-First Search (BFS):

Breadth-First Search (BFS) is a traversal algorithm used to explore nodes of a graph or tree data structure. It starts at a selected node and explores all its neighbors at the current depth before moving on to nodes at the next depth level.

BFS can be implemented using a queue data structure to keep track of nodes to visit. It ensures that nodes are visited in a breadth-wise manner, i.e., nodes at the same level are visited before moving on to the next level.

Input / Output:

Input: A graph or tree data structure and a starting node.
Output: The nodes visited in the order they were explored.

Explanation:

- Start at the selected node and mark it as visited.
- Explore all the unvisited neighboring nodes of the current node.
- Add these neighboring nodes to a queue.
- Remove the first node from the queue and mark it as visited.
- Repeat steps 2-4 until the queue is empty.

```javascript
class Graph {
  constructor() {
    this.adjacencyList = {};
  }

  // Add a vertex to the graph
  addVertex(vertex) {
    if (!this.adjacencyList[vertex]) {
      this.adjacencyList[vertex] = [];
    }
  }

  // Add an edge between two vertices
  addEdge(vertex1, vertex2) {
    this.adjacencyList[vertex1].push(vertex2);
    this.adjacencyList[vertex2].push(vertex1); // For undirected graph
  }

  // Breadth-First Search
  bfs(start) {
    const visited = {};
    const result = [];
    const queue = [start];

    visited[start] = true;

    while (queue.length) {
      const currentVertex = queue.shift();
      result.push(currentVertex);

      this.adjacencyList[currentVertex].forEach((neighbor) => {
        if (!visited[neighbor]) {
          visited[neighbor] = true;
          queue.push(neighbor);
        }
      });
    }

    return result;
  }
}

// Example usage:
const graph = new Graph();
graph.addVertex("A");
graph.addVertex("B");
graph.addVertex("C");
graph.addVertex("D");
graph.addVertex("E");
graph.addEdge("A", "B");
graph.addEdge("A", "C");
graph.addEdge("B", "D");
graph.addEdge("C", "E");

console.log(graph.bfs("A"));
```
