# AnandOnDSA

## Topics

> Recursion Fundamentals
1. Factorial
2. Fibonacci
3. Tower of Hanoi

> Basic Data Structures
1. Arrays
2. Singly Linked Lists
3. Doubly Linked Lists
4. Circular Linked Lists
5. Stacks
6. Queues
7. Hash Table
8. Hash Maps
9. Hash Sets

> Advanced Data Structures
1. Binary Tree
2. Binary Search Tree
3. AVL Tree
4. Segment Tree
5. Fenwick Tree
6. Graphs (Adjacency Matrix/List)
7. Depth First Search (DFS)
8. Breadth FIrst Search (BFS)
9. Shortest Path Algorithms
10. Heaps
11. Min-Heap
12. Max-Heap
13. Priority Queues
14. Tries (Prefix Trees)
15. Disjoint Sets (Union-Find)

> Sorting Algorithms
1. Bubble Sort
2. Selection Sort
3. Insertion Sort
4. Merge Sort
5. Quick Sort
6. Heap Sort
7. Counting Sort
8. Radix Sort

> Searching Algorithms
1. Linear Search
2. Binary Search
3. Search Variations (in Rotated Arrays, Matrix)

> Specialized Algorithms
1. String Matching - KMP
2. String Matching - Rabin-Karp
3. String Matching - Z-Algorithm
4. Graph Algorithms - Dijkstra’s
5. Graph Algorithms - Bellman-Ford
6. Graph Algorithms - Floyd-Warshall
7. Graph Algorithms - Kruskal’s
8. Graph Algorithms - Prim’s
9. Topological Sorting
10. Minimum Spanning Tree

> Key Algorithmic Paradigms
1. Divide and Conquer
2. Greedy Algorithms
3. Sliding Window Technique
4. Two Pointers Technique
5. Bit Manipulation
6. Kadane’s Algorithm
7. Floyd’s Cycle Detection
8. Sliding Window Problems
9. Subset Problems

> Dynamic Programming (DP)
1. Top-Down (Memoization) vs Bottom-Up (Tabulation)
2. Optimal Substructure and Overlapping Subproblems
3. Fibonacci Sequence
4. Longest Common Subsequence (LCS)
5. Longest Increasing Subsequence (LIS)
6. 0/1 Knapsack Problem
7. Matrix Chain Multiplication
8. Subset Sum Problem
9. Partition Equal Subset Sum
10. Edit Distance
11. Rod Cutting Problem
12. Egg Dropping Problem
13. Wildcard Matching
14. Grid/Matrix - Unique Paths
15. Grid/Matrix - Minimum Path Sum
16. Grid/Matrix - Maximal Square
17. Longest Palindromic Subsequence
18. Longest Palindromic Substring


### Factorial
Factorial is a simple problem implemented with recursion

```java
private static int factorial(int n) {
  if (n<=1) return 1;
  return n*factorial(n-1);
}
```
### Fibonacci
Fibonacci is a famous problem based on golden ratio. Where an element is sum of previous two elements.
0 1 1 2 3 5 8 13 21 34 ...
```java
private static void fibonacci(int n) {
  fibonacciRecursion(n, 0, 1);
}

private static void fibonacciRecursion(int count, int n1, int n2) {
  if (count<=0) return;
  System.out.println(n1);
  fibonacciRecursion(count-1, n2, n1+n2);
}
```
### Tower of Hanoi

### Arrays
Arrays are sequence of elements based on indexes.
```java
import java.util.Arrays;

public class Main {
  public static void main(String[] args) {
    int[] data = {1, 6, 8, 2, 0, 9, 4};
    Arrays.sort(data);
    System.out.println(Arrays.toString(data));
    System.out.println(Arrays.binarySearch(data, 8));
  }
}
```

### Dynamic Array ( ArrayList )
Instead of fixes size. The size is dynamically increased. In Java **ArrayList** provides that support by default.
Initial **capacity is 10** by default. While adding more data, the size increased, by **grow & shrink** technique.
```java
grow = (capcity) -> { capacity*2 };
shrink = (capcity) -> { capacity/2 };
```
We can provide custom capacity size while creating ArrayList in Java
```java
ArrayList<Integer> list = new ArrayList<>(20);
```

### Singly Linked Lists
Dynamic Array size. So less memory comparing with Array. Insertion & deletion will be O(1) if we know the pointer location.
But it carries extra memory for pointers as well. Searching an element will be O(n).
```mermaid
graph LR;
    A[A.Head :10] --> B[B :20];
    B --> C[C :30];
    C --> Tail[D.Tail :null];
```
Data structure goes like below.
```java
class Node {
  int value;
  Node next;
  Node(int value) {
    this.value = value;
  }
}

class SingleLinkedList {
  Node head;
  Node tail;
  
  SingleLinkedList() {}
  
  public void addData(int value) {
    Node newNode = new Node(value);
    if (this.head == null) {
      newNode.next = this.tail;
      this.head = newNode;
    } else {
      newNode.next = this.head.next;
      this.head.next = newNode;
    }
  }
}
```
And Java provides default implementation as well.
```java
LinkedList<String> ll = new LinkedList<String>();
ll.add("A");
ll.remove("A");
```
It can act as Stack & Queue also.
```java
\\ Stack
ll.push("S");
ll.pop();

\\ Queue
ll.offer("S");
ll.poll();
```
Provides more simple features comparing with Arrays, such as
```java
.addFirst("x");
.addLast("x");
.removeFirst("x");
.removeLast("x");
.getFirst();
.getLast();
```

### Doubly Linked Lists
```mermaid
graph LR;
    A[A.Head :10] <--> B[B :20];
    B <--> C[C :30];
    C <--> Tail[D.Tail :null];
```
In this structure each node has prev & next pointers addressing to previous and next nodes.
```java
class Node {
  Node prev;
  int value;
  Node next;
  Node(int value) {
    this.value = value;
  }
}

class DoubleLinkedList {
  Node head;
  Node tail;
  
  DoubleLinkedList() {}
  
  public void addData(int value) {
    Node newNode = new Node(value);
    if (this.head == null) {
      this.head = newNode;
      this.tail = newNode;
    } else {
      this.tail.next = newNode;
      newNode.prev = this.tail;
      this.tail = newNode;
    }
  }
}
```
The same LinkedList class in Java provide **bidirection traversal** support for double linked list.

```java
LinkedList<String> ll = new LinkedList<String>();
ll.add("A");
ll.remove("A");
```

### Circular Linked Lists

### Stacks
Last In First Out (LIFO) Structure based.
```java
static class Stack {
    int[] data;
    int pointer;
    int capacity = 100;
    
    Stack() {
      data = new int[capacity];
      pointer = -1;
    }
    void push(int value) {
      if (pointer>=capacity) {
        capacity *= 2;
        this.data = Arrays.copyOf(this.data, capacity);
      }
      pointer++;
      data[pointer] = value;
    }
    int pop() {
      if (pointer>0) {
        int value = this.data[pointer];
        pointer--;
        return value;
      }
      return -1;
    }
    void display() {
      System.out.println("\nStack:");
      for (int i=0; i<=this.pointer; i++) {
        System.out.println(this.data[i]);
      }
    }
  }
```

### Top-Down (Memoization) vs Bottom-Up (Tabulation)
**Top-Down (Memoization):**
This approach involves solving the problem recursively and storing the results of subproblems to avoid redundant computations.
```python
def fib_memo(n, memo={}):
    if n in memo:
        return memo[n]
    if n <= 1:
        return n
    memo[n] = fib_memo(n-1, memo) + fib_memo(n-2, memo)
    return memo[n]

print(fib_memo(10))  # Output: 55
```
**Bottom-Up (Tabulation):**
```python
def fib_tab(n):
    if n <= 1:
        return n
    dp = [0] * (n + 1)
    dp[1] = 1
    for i in range(2, n + 1):
        dp[i] = dp[i-1] + dp[i-2]
    return dp[n]

print(fib_tab(10))  # Output: 55
```

### Optimal Substructure and Overlapping Subproblems
**Optimal Substructure:** A problem has optimal substructure if an optimal solution can be constructed from optimal solutions of its subproblems.
**Overlapping Subproblems:** A problem has overlapping subproblems if the same subproblems are solved multiple times.

### Fibonacci Sequence
**Top-Down (Memoization):**
```python
def fib_memo(n, memo={}):
    if n in memo:
        return memo[n]
    if n <= 1:
        return n
    memo[n] = fib_memo(n-1, memo) + fib_memo(n-2, memo)
    return memo[n]

print(fib_memo(10))  # Output: 55
```
**Bottom-Up (Tabulation):**
```python
def fib_tab(n):
    if n <= 1:
        return n
    dp = [0] * (n + 1)
    dp[1] = 1
    for i in range(2, n + 1):
        dp[i] = dp[i-1] + dp[i-2]
    return dp[n]

print(fib_tab(10))  # Output: 55
```

### Longest Common Subsequence (LCS)
```python
def lcs(X, Y):
    m, n = len(X), len(Y)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if X[i-1] == Y[j-1]:
                dp[i][j] = dp[i-1][j-1] + 1
            else:
                dp[i][j] = max(dp[i-1][j], dp[i][j-1])
    return dp[m][n]

print(lcs("ABCBDAB", "BDCAB"))  # Output: 4
```
### Longest Increasing Subsequence (LIS)
```python
def lis(arr):
    n = len(arr)
    dp = [1] * n
    for i in range(1, n):
        for j in range(i):
            if arr[i] > arr[j]:
                dp[i] = max(dp[i], dp[j] + 1)
    return max(dp)

print(lis([10, 22, 9, 33, 21, 50, 41, 60, 80]))  # Output: 6
```

### 0/1 Knapsack Problem
```python
def knapsack(W, wt, val, n):
    dp = [[0 for _ in range(W + 1)] for _ in range(n + 1)]
    for i in range(n + 1):
        for w in range(W + 1):
            if i == 0 or w == 0:
                dp[i][w] = 0
            elif wt[i-1] <= w:
                dp[i][w] = max(val[i-1] + dp[i-1][w-wt[i-1]], dp[i-1][w])
            else:
                dp[i][w] = dp[i-1][w]
    return dp[n][W]

print(knapsack(50, [10, 20, 30], [60, 100, 120], 3))  # Output: 220
```

### Matrix Chain Multiplication
```python
def matrix_chain_order(p):
    n = len(p) - 1
    dp = [[0] * n for _ in range(n)]
    for l in range(2, n + 1):
        for i in range(n - l + 1):
            j = i + l - 1
            dp[i][j] = float('inf')
            for k in range(i, j):
                q = dp[i][k] + dp[k+1][j] + p[i] * p[k+1] * p[j+1]
                if q < dp[i][j]:
                    dp[i][j] = q
    return dp[0][n-1]

print(matrix_chain_order([1, 2, 3, 4]))  # Output: 18
```

### Subset Sum Problem
```python
def is_subset_sum(arr, sum):
    n = len(arr)
    dp = [[False] * (sum + 1) for _ in range(n + 1)]
    for i in range(n + 1):
        dp[i][0] = True
    for i in range(1, n + 1):
        for j in range(1, sum + 1):
            if j < arr[i-1]:
                dp[i][j] = dp[i-1][j]
            else:
                dp[i][j] = dp[i-1][j] or dp[i-1][j-arr[i-1]]
    return dp[n][sum]

print(is_subset_sum([3, 34, 4, 12, 5, 2], 9))  # Output: True
```
### Partition Equal Subset Sum
```python
def can_partition(nums):
    total_sum = sum(nums)
    if total_sum % 2 != 0:
        return False
    subset_sum = total_sum // 2
    dp = [False] * (subset_sum + 1)
    dp[0] = True
    for num in nums:
        for i in range(subset_sum, num - 1, -1):
            dp[i] = dp[i] or dp[i - num]
    return dp[subset_sum]

print(can_partition([1, 5, 11, 5]))  # Output: True
```

### Edit Distance
```python
def edit_distance(str1, str2):
    m, n = len(str1), len(str2)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    for i in range(m + 1):
        for j in range(n + 1):
            if i == 0:
                dp[i][j] = j
            elif j == 0:
                dp[i][j] = i
            elif str1[i-1] == str2[j-1]:
                dp[i][j] = dp[i-1][j-1]
            else:
                dp[i][j] = 1 + min(dp[i-1][j], dp[i][j-1], dp[i-1][j-1])
    return dp[m][n]

print(edit_distance("kitten", "sitting"))  # Output: 3
```
### Rod Cutting Problem
```python
def rod_cutting(price, n):
    dp = [0] * (n + 1)
    for i in range(1, n + 1):
        max_val = float('-inf')
        for j in range(i):
            max_val = max(max_val, price[j] + dp[i-j-1])
        dp[i] = max_val
    return dp[n]

print(rod_cutting([1, 5, 8, 9, 10, 17, 17, 20], 8))  # Output: 22
```

### Egg Dropping Problem
```python
def egg_drop(n, k):
    dp = [[0] * (k + 1) for _ in range(n + 1)]
    for i in range(1, n + 1):
        for j in range(1, k + 1):
            if i == 1:
                dp[i][j] = j
            elif j == 1:
                dp[i][j] = 1
            else:
                dp[i][j] = float('inf')
                for x in range(1, j + 1):
                    res = 1 + max(dp[i-1][x-1], dp[i][j-x])
                    if res < dp[i][j]:
                        dp[i][j] = res
    return dp[n][k]

print(egg_drop(2, 10))  # Output: 4
```

### Wildcard Matching
```python
def is_match(s, p):
    m, n = len(s), len(p)
    dp = [[False] * (n + 1) for _ in range(m + 1)]
    dp[0][0] = True
    for j in range(1, n + 1):
        if p[j-1] == '*':
            dp[0][j] = dp[0][j-1]
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if p[j-1] == '*':
                dp[i][j] = dp[i][j-1] or dp[i-1][j]
            elif p[j-1] == '?' or s[i-1] == p[j-1]:
                dp[i][j] = dp[i-1][j-1]
    return dp[m][n]

print(is_match("adceb", "*a*b"))  # Output: True
```

### Grid/Matrix - Unique Paths
```python
def unique_paths(m, n):
    dp = [[1] * n for _ in range(m)]
    for i in range(1, m):
        for j in range(1, n):
            dp[i][j] = dp[i-1][j] + dp[i][j-1]
    return dp[m-1][n-1]

print(unique_paths(3, 7))  # Output: 28
```

### Grid/Matrix - Minimum Path Sum
```python
def min_path_sum(grid):
    m, n = len(grid), len(grid[0])
    dp = [[0] * n for _ in range(m)]
    dp[0][0] = grid[0][0]
    for i in range(1, m):
        dp[i][0] = dp[i-1][0] + grid[i][0]
    for j in range(1, n):
        dp[0][j] = dp[0][j-1] + grid[0][j]
    for i in range(1, m):
        for j in range(1, n):
            dp[i][j] = min(dp[i-1][j], dp[i][j-1]) + grid[i][j]
    return dp[m-1][n-1]

print(min_path_sum([[1,3,1],[1,5,1],[4,2,1]]))  # Output: 7
```

### Grid/Matrix - Maximal Square
```python
def maximal_square(matrix):
    if not matrix:
        return 0
    m, n = len(matrix), len(matrix[0])
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    max_side = 0
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if matrix[i-1][j-1] == '1':
                dp[i][j] = min(dp[i-1][j], dp[i][j-1], dp[i-1][j-1]) + 1
                max_side = max(max_side, dp[i][j])
    return max_side * max_side

print(maximal_square([
    ["1","0","1","0","0"],
    ["1","0","1","1","1"],
    ["1","1","1","1","1"],
    ["1","0","0","1","0"]
]))  # Output: 4
```

### Longest Palindromic Subsequence
```python
def longest_palindromic_subseq(s):
    n = len(s)
    dp = [[0] * n for _ in range(n)]
    for i in range(n):
        dp[i][i] = 1
    for cl in range(2, n + 1):
        for i in range(n - cl + 1):
            j = i + cl - 1
            if s[i] == s[j] and cl == 2:
                dp[i][j] = 2
            elif s[i] == s[j]:
                dp[i][j] = dp[i+1][j-1] + 2
            else:
                dp[i][j] = max(dp[i][j-1], dp[i+1][j])
    return dp[0][n-1]

print(longest_palindromic_subseq("bbbab"))  # Output: 4
```

### Longest Palindromic Substring
```python
def longest_palindromic_substring(s):
    n = len(s)
    if n == 0:
        return ""
    dp = [[False] * n for _ in range(n)]
    start, max_length = 0, 1
    for i in range(n):
        dp[i][i] = True
    for i in range(n-1):
        if s[i] == s[i+1]:
            dp[i][i+1] = True
            start = i
            max_length = 2
    for length in range(3, n + 1):
        for i in range(n - length + 1):
            j = i + length - 1
            if dp[i+1][j-1] and s[i] == s[j]:
                dp[i][j] = True
                start = i
                max_length = length
    return s[start:start + max_length]

print(longest_palindromic_substring("babad"))  # Output: "bab" or "aba"
```
