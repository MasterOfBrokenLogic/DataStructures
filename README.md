# Data Structures - BCA (Hons) Second Semester Exam - Model Answers

> **University:** Mahatma Gandhi University  
> **Course:** MG2CCRBCA101 - Data Structures  
> **Max Marks:** 70  
> **Duration:** 2 hours

---

### Q1. Differentiate between linear and non-linear Data Structures
Linear data structures store data sequentially, like elements in an array `[1, 2, 3, 4]` or a linked list where each node points to the next. Non-linear data structures organize data in a hierarchical manner like a tree or connect data freely like a graph. For example, in a binary tree, each parent connects to two children.

### Q2. How does the pop operation change the state of the stack in an array-based implementation?
In a stack implemented with an array, a pop operation removes the top element and decreases the size by one. The top pointer moves to the previous element.

```c
// Example:
int Stack[] = {5, 10, 15};
// After pop
// Stack becomes {5, 10}
```

### Q3. Define a linked list and explain its basic structure
A linked list is made of nodes, each containing data and a pointer to the next node. It allows dynamic memory allocation and easy insertion/deletion.

```c
Example: 10 -> 20 -> 30 -> NULL
```

### Q4. What is a walk in a graph? How does it differ from a path?
A walk in a graph is a sequence where vertices and edges may repeat. A path is a walk with no repeated vertices.

```c
Example:
Walk: A -> B -> C -> A
Path: A -> B -> C
```

### Q5. Discuss the disadvantages of Binary Search
Binary Search can only work on sorted data. If the array is unsorted, extra time is needed for sorting. It also requires direct access to elements like arrays, not linked lists.

```c
Example:
Sorted Array: [1,3,5,7,9] → Binary Search works
Unsorted Array: [5,2,9,1] → Need to sort first
```

### Q6. Differentiate between best-case and worst-case complexities
Best-case complexity is the least time or space an algorithm needs for the easiest input, while worst-case complexity is the most time or space it needs for the hardest input. We usually focus on worst-case because it shows the maximum effort the algorithm will ever need.

```c
Example:
Searching for 1 in array [1,2,3,4]
Best-case: Found at first position → O(1)
Worst-case: Found at last or not found → O(n)
```

### Q7. Compare postfix and infix notation
### Infix Notation
In infix notation, the operator is placed between the operands (e.g., A + B). This is the common way we write expressions, but it requires parentheses and operator precedence to determine the correct order of operations.

### Postfix Notation
In postfix notation, the operator is placed after the operands (e.g., A B +). It is simpler to evaluate using a stack and doesn't require parentheses or precedence rules.

```c
Example:
Infix: (5 + 6) * 7 // Infix notation requires parentheses to indicate the order of operations.
Postfix: 5 6 + 7 * // Postfix notation places operators after operands, eliminating the need for parentheses.
```

### Q8. Explain circular linked list
A circular linked list connects the last node back to the first node instead of NULL, forming a circle. It is used in scheduling systems like playlists.

```c
Example:
10 -> 20 -> 30 -> 10
```

### Q9. Recursive vs Iterative Implementation

## Recursive Implementation
In a recursive implementation, a function calls itself to solve smaller instances of a problem. This approach typically involves a base case to stop the recursion. Recursive solutions are elegant and easy to understand for problems that can be broken down into smaller subproblems (like tree traversal or factorial calculation).

### Example:
```c
// Recursive Factorial
int factorial(int n) {
    if (n == 0) return 1;
    return n * factorial(n-1);
}
```

## Iterative Implementation
In an iterative implementation, a loop (such as for or while) is used to repeat a set of operations until a condition is met. Iteration is generally more efficient in terms of memory usage because it does not involve function calls, which can lead to stack overflow in deep recursion.

Example:
```c
// Iterative Factorial
int factorial_iter(int n) {
    int result = 1;
    for (int i = 1; i <= n; i++)
        result *= i;
    return result;
}
```
Key Differences:
- Memory Usage: Recursive methods use more memory due to function call stacks, while iterative methods use less memory.
- Performance: Iterative methods are usually faster and more memory-efficient for large input sizes, as recursion may lead to stack overflow or higher overhead.
- Ease of Understanding: Recursion often provides a more natural and cleaner solution for problems that are inherently recursive, such as tree traversal or factorial calculation.

### Q10. Insertion Sort vs Selection Sort
## Insertion Sort
**Definition:**  
Insertion Sort builds the sorted portion of the array one element at a time by inserting each element into its correct position relative to the already sorted elements. It is efficient for small datasets or partially sorted arrays.

### Key Operation:
- **Job:** For each element, it compares it with the previous elements and shifts them to the right until it finds the correct position for the current element.

```c
int key = arr[i]; 
int j = i - 1;
while (j >= 0 && arr[j] > key) { 
    arr[j + 1] = arr[j]; 
    j = j - 1; 
}
arr[j + 1] = key;
```

## Selection Sort
**Definition:**
Selection Sort repeatedly finds the minimum element from the unsorted portion of the array and swaps it with the first unsorted element. It is easy to implement but inefficient for large datasets.

### Key Operation:
- **Job:** For each position in the array, it searches the minimum element in the remaining unsorted portion and swaps it with the current position.

```c
int minIndex = i;
for (int j = i + 1; j < n; j++) {
    if (arr[j] < arr[minIndex]) {
        minIndex = j;
    }
}
int temp = arr[minIndex];
arr[minIndex] = arr[i];
arr[i] = temp;
```

### Key Differences:
- **Insertion Sort**: Insertion-based, builds the sorted array incrementally by inserting each element in its correct position.
- **Selection Sort:** Selection-based, finds the minimum element from the unsorted part and swaps it with the current element.

### Q11. Array implementation of simple and circular queue
## Simple Queue
**Definition:**
A Simple Queue is a data structure that follows the FIFO (First In, First Out) rule. This means the first item added to the queue will be the first one to be removed. Items are added at the end and removed from the front. When you remove an item, the other items have to shift forward, which can take extra time.

```c
// Simple Queue
int queue[5];
int front = -1, rear = -1;
rear++;
queue[rear] = 10;
rear++;
queue[rear] = 20;
front++;
int removed = queue[front];
```
## Circular Queue:
**Definition:** 
A Circular Queue is similar to a simple queue, but it makes better use of space. When the queue reaches the end of the array, it starts over from the beginning. This way, there’s no need to shift items when removing one, and it avoids wasting space. It still follows the FIFO rule: first item added, first item removed.
```c
// Circular Queue
int size = 5;
front = (front + 1) % size;
rear = (rear + 1) % size;
queue[rear] = 30;
```

### Q12. Insertion in AVL Tree
An **AVL Tree** is a special type of binary search tree that keeps itself balanced. When you insert a new node, it is placed like in a normal binary search tree. After that, the tree checks if it’s still balanced. If any part of the tree is too unbalanced, it fixes it by rotating parts of the tree to restore balance. This ensures that the tree always stays balanced, making search operations faster.

```c
Example:
Insert 10, 20, 30 → Right-Right imbalance → Apply Left Rotation
Resulting Tree:
    20
   /  \
 10   30
```

### Q13. Merging two sorted arrays
Merging two sorted arrays involves combining two already sorted arrays into one single sorted array. You compare the elements from both arrays, adding the smaller element to the result array one by one, until all elements from both arrays are processed.

```c
int arr1[] = {1, 3, 5, 7};
int arr2[] = {2, 4, 6, 8};
int merged[8];  // Array to store the merged result
int i = 0, j = 0, k = 0;

// Compare elements from both arrays and add the smaller one to merged
while (i < 4 && j < 4) {
    if (arr1[i] < arr2[j]) {
        merged[k++] = arr1[i++];
    } else {
        merged[k++] = arr2[j++];
    }
}

// Copy remaining elements from arr1
while (i < 4) {
    merged[k++] = arr1[i++];
}

// Copy remaining elements from arr2
while (j < 4) {
    merged[k++] = arr2[j++];
}

// Printing merged array
for (int l = 0; l < 8; l++) {
    printf("%d ", merged[l]);
}
```
```c
Output:
1 2 3 4 5 6 7 8
```

### Q14. Compare circular queue, deque, and priority queue
# Comparison of Circular Queue, Deque, and Priority Queue

## Circular Queue
- **Type**: Linear Queue with Circular behavior.
- **Use**: Efficient space utilization by wrapping around the array when the end is reached.
- **Operations**: 
  - Enqueue and dequeue from both ends.
  - No random access.
- **Example**: Round-robin scheduling.

## Deque (Double-Ended Queue)
- **Type**: Linear, with both ends available for insertion and deletion.
- **Use**: More flexible than a regular queue.
- **Operations**: 
  - Can enqueue and dequeue from both the front and rear.
- **Example**: Scenarios needing both ends to be accessed efficiently.

## Priority Queue
- **Type**: Special queue with prioritized elements.
- **Use**: Elements are dequeued based on priority, not order of insertion.
- **Operations**: 
  - Dequeue elements based on priority.
- **Example**: Task scheduling in operating systems with priorities.

### Q15. Hashing and collision handling
# Hashing and Collision Handling

## Hashing
**Hashing** is a method of converting data into a fixed-size value called a **hash code**. This hash code helps quickly store and retrieve data in a **hash table** using a **hash function**.

## Collision Handling
A **collision** happens when two different pieces of data produce the same hash code. Here are two ways to handle collisions:

### 1. Chaining
- Each index in the hash table holds a list. When a collision happens, the new element is added to the list at that index.

### 2. Open Addressing
- When a collision occurs, the algorithm searches for the next available slot in the hash table. Some common methods are:
  - **Linear Probing**: Check the next index one by one.
  - **Quadratic Probing**: Use a specific pattern to find the next index.
  - **Double Hashing**: Use another hash function to find the next available index.

## Example:
- **Hashing**: A key `25` might give an index `5`.
- **Collision Handling (Chaining)**: If another key also hashes to `5`, it’s added to a list at index `5`.
- **Collision Handling (Open Addressing)**: If index `5` is already taken, the next available index is tried.

### Q16. Explain binary tree traversal methods
## Inorder Traversal (Left, Root, Right)
**Definition**:  
In **Inorder Traversal**, the tree is traversed starting from the **left** subtree, moving to the **root** node, and then visiting the **right** subtree. This is a **depth-first** traversal method. 

- In **binary search trees (BST)**, **inorder traversal** visits nodes in **ascending order**. This makes it especially useful for tasks that require sorted data.
- It’s often used when you need to **print** or **retrieve elements** of a BST in order.

### Example:
```c
For the tree:
    1
   / \
  2   3
 / \
4   5
```
**Inorder Traversal** would visit the nodes in this order: `4, 2, 5, 1, 3`.

---

## Preorder Traversal (Root, Left, Right)
**Definition**:  
In **Preorder Traversal**, the nodes are visited in the following order: **root**, **left subtree**, and then **right subtree**. This method is also **depth-first**. The key property is that the root node is processed **before** its children.

- **Preorder** is commonly used when you need to **copy** the structure of a tree, or for situations where **expression trees** (e.g., algebraic expressions) are being evaluated or built.
- It’s also helpful for creating a **clone** of a tree.

### Example:
```c
For the tree:
    1
   / \
  2   3
 / \
4   5
```
**Preorder Traversal** would visit the nodes in this order: `1, 2, 4, 5, 3`.

---

## Postorder Traversal (Left, Right, Root)
**Definition**:  
In **Postorder Traversal**, the nodes are visited in this order: **left subtree**, **right subtree**, and then **root**. This is a **depth-first** traversal where the root node is processed **after** its children.

- **Postorder** is mainly used when you need to **delete** nodes or evaluate **postfix expressions**. It's useful when performing tasks like memory management (e.g., deleting nodes) or calculating tree-related values in a bottom-up manner.
- It’s the opposite of **preorder** because it processes the root node **last**.

### Example:
```c
For the tree:
    1
   / \
  2   3
 / \
4   5
```
**Postorder Traversal** would visit the nodes in this order: `4, 5, 2, 3, 1`.

---

## Level-order Traversal (Breadth-First)
**Definition**:  
In **Level-order Traversal**, nodes are visited level by level, from left to right, starting at the root. This is a **breadth-first** traversal method, which explores all nodes at a given level before moving to the next level.

- Level-order traversal is often implemented using a **queue** data structure to track the nodes in each level.
- This traversal is useful in scenarios such as **finding the shortest path** or determining the **minimum depth** of the tree. It’s also used in **graph traversal algorithms**.

### Example:
```c
For the tree:
    1
   / \
  2   3
 / \
4   5
```
**Level-order Traversal** would visit the nodes in this order: `4, 5, 2, 3, 1`.

## Summary of Traversal Methods:

- **Inorder Traversal (Left → Root → Right)**: Visit left subtree, root, and then right subtree. It’s used in BSTs to retrieve elements in **ascending order**.
- **Preorder Traversal (Root → Left → Right)**: Visit root first, then left and right subtrees. It’s used to **copy** or **create** trees, and in **expression trees**.
- **Postorder Traversal (Left → Right → Root)**: Visit left subtree, right subtree, and then root. It’s used to **delete nodes** or evaluate **postfix expressions**.
- **Level-order Traversal (Breadth-First)**: Visit nodes level by level, from left to right. It’s useful for **finding the shortest path** or **minimum depth**.
