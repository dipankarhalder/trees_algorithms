### Trees Algorithms

#### 1. Depth-First Search (DFS)

Depth-First Search (DFS) is a popular graph traversal algorithm used to explore or search through a graph or tree data structure. It starts at a selected node (or vertex) and explores as far as possible along each branch before backtracking. This algorithm is implemented using a stack data structure.

Steps:

- Start at a selected node (usually the root node).
- Mark the node as visited.
- Explore each neighbor of the current node recursively that has not been visited.
- Repeat the process until all nodes have been visited.

```javascript
// Node class to represent a graph node
class Node {
  constructor(value) {
    this.value = value;
    this.adjacentNodes = [];
    this.visited = false;
  }

  // Method to add an adjacent node
  addAdjacent(node) {
    this.adjacentNodes.push(node);
  }
}

// DFS function
function dfs(node) {
  if (!node) return;

  // Mark the current node as visited
  node.visited = true;
  console.log("Visited node:", node.value);

  // Explore adjacent nodes
  for (let adjacentNode of node.adjacentNodes) {
    if (!adjacentNode.visited) {
      dfs(adjacentNode);
    }
  }
}

// Example usage:
// Create graph nodes
const node1 = new Node(1);
const node2 = new Node(2);
const node3 = new Node(3);
const node4 = new Node(4);
const node5 = new Node(5);

// Add edges between nodes
node1.addAdjacent(node2);
node1.addAdjacent(node3);
node2.addAdjacent(node4);
node2.addAdjacent(node5);
node3.addAdjacent(node5);

// Perform DFS starting from node1
console.log("DFS traversal:");
dfs(node1);
```

#### 2. Breadth-First Search (BFS)

Breadth-First Search (BFS) is another popular graph traversal algorithm used to explore or search through a graph or tree data structure. Unlike DFS, BFS explores neighbors of a node before moving on to the next level of neighbors. It is implemented using a queue data structure.

Steps:

- Start at a selected node (usually the root node).
- Enqueue the starting node into a queue and mark it as visited.
- Dequeue a node from the queue and explore its neighbors.
- Enqueue all unvisited neighbors into the queue and mark them as visited.
- Repeat the process until the queue is empty.

```javascript
// Node class to represent a graph node
class Node {
  constructor(value) {
    this.value = value;
    this.adjacentNodes = [];
    this.visited = false;
  }

  // Method to add an adjacent node
  addAdjacent(node) {
    this.adjacentNodes.push(node);
  }
}

// BFS function
function bfs(startNode) {
  if (!startNode) return;

  const queue = [];

  // Enqueue the starting node
  queue.push(startNode);
  startNode.visited = true;

  // BFS traversal
  while (queue.length > 0) {
    // Dequeue a node
    const currentNode = queue.shift();
    console.log("Visited node:", currentNode.value);

    // Enqueue unvisited neighbors
    for (let adjacentNode of currentNode.adjacentNodes) {
      if (!adjacentNode.visited) {
        queue.push(adjacentNode);
        adjacentNode.visited = true;
      }
    }
  }
}

// Example usage:
// Create graph nodes
const node1 = new Node(1);
const node2 = new Node(2);
const node3 = new Node(3);
const node4 = new Node(4);
const node5 = new Node(5);

// Add edges between nodes
node1.addAdjacent(node2);
node1.addAdjacent(node3);
node2.addAdjacent(node4);
node2.addAdjacent(node5);
node3.addAdjacent(node5);

// Perform BFS starting from node1
console.log("BFS traversal:");
bfs(node1);
```
