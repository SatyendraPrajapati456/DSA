# Segment Tree Implementation! - Java

## 1. Problem Details

**Platform:** GeeksforGeeks

**Question Link:**
https://www.geeksforgeeks.org/problems/range-minimum-query/1

**Question Name:** Segment Tree Implementation! - Java

**Question Description:**

Refer to GeeksforGeeks problem statement.

## 2. Test Cases

### Test Case 1: Standard Range Minimum Query

Input:
```text
arr = [1, 3, 2, 7, 9, 11], queries = [(1, 4)]
```

Output:
```text
2
```

Explanation:
The subarray from index 1 to 4 is [3, 2, 7, 9], and the minimum value in this range is 2.

### Test Case 2: Single Element Range

Input:
```text
arr = [5, 2, 4], queries = [(1, 1)]
```

Output:
```text
2
```

Explanation:
The range covers only index 1, where the value is 2.

### Test Case 3: Full Array Range

Input:
```text
arr = [4, 6, 1, 9], queries = [(0, 3)]
```

Output:
```text
1
```

Explanation:
The entire array is queried, and the minimum element is 1.

## 3. AI-Generated Approach

### Approach: Segment Tree

Use a segment tree to efficiently answer range minimum queries on an array with logarithmic time complexity for queries and linear time for building.

**Step-by-Step Reasoning:**
1. Initialize a segment tree array of size roughly four times the input array size.
2. Recursively build the segment tree by dividing the array into halves and storing the minimum of both halves at each parent node.
3. For a range minimum query, recursively check node intervals. Return the identity element (Integer.MAX_VALUE) if out of bounds, the node value if fully inside the query range, or combine results from left and right children if partially overlapping.

**Why It Works:**
The segment tree divides the range into O(log N) canonical subranges. By leveraging precomputed minimums at each node, range queries avoid linear scans and prune recursion paths that do not overlap with the query interval.

### Time Complexity

O(log N) per query, O(N) to build

### Space Complexity

O(N)

## 4. Java Solution

### Required Concepts

- Segment Tree
- Divide and Conquer
- Recursion

### Original Accepted Submission

```java
return ans;
    }

    public void buildTree(int[] arr, int node, int left, int right) {

        if (left == right) {
            tree[node] = arr[left];
            return;
        }

        int mid = left + (right - left) / 2;

        buildTree(arr, 2 * node + 1, left, mid);
        buildTree(arr, 2 * node + 2, mid + 1, right);

        tree[node] = Math.min(tree[2 * node + 1], tree[2 * node + 2]);
    }

    public int query(int node, int left, int right, int from, int to) {

        if (to < left || right < from) {
            return Integer.MAX_VALUE;
        }

        if (from <= left && right <= to) {
            return tree[node];
        }

        int mid = left + (right - left) / 2;

        int leftdir = query(2 * node + 1, left, mid, from, to);

        int rightdir = query(2 * node + 2, mid + 1, right, from, to);

        return Math.min(leftdir, rightdir);
    }
}
```

### AI-Generated Java Alternative

```java
class Solution {
    int[] tree;

    public void buildTree(int[] arr, int node, int left, int right) {
        if (left == right) {
            tree[node] = arr[left];
            return;
        }
        int mid = left + (right - left) / 2;
        buildTree(arr, 2 * node + 1, left, mid);
        buildTree(arr, 2 * node + 2, mid + 1, right);
        tree[node] = Math.min(tree[2 * node + 1], tree[2 * node + 2]);
    }

    public int query(int node, int left, int right, int from, int to) {
        if (to < left || right < from) {
            return Integer.MAX_VALUE;
        }
        if (from <= left && right <= to) {
            return tree[node];
        }
        int mid = left + (right - left) / 2;
        int leftdir = query(2 * node + 1, left, mid, from, to);
        int rightdir = query(2 * node + 2, mid + 1, right, from, to);
        return Math.min(leftdir, rightdir);
    }
}
```

## 5. Python Solution

### Required Concepts

- Lists
- Recursion
- Range Queries

### AI-Generated Python Implementation

```python
class Solution:
    def __init__(self, arr):
        n = len(arr)
        self.tree = [0] * (4 * n)
        self.buildTree(arr, 0, 0, n - 1)

    def buildTree(self, arr, node, left, right):
        if left == right:
            self.tree[node] = arr[left]
            return
        mid = left + (right - left) // 2
        self.buildTree(arr, 2 * node + 1, left, mid)
        self.buildTree(arr, 2 * node + 2, mid + 1, right)
        self.tree[node] = min(self.tree[2 * node + 1], self.tree[2 * node + 2])

    def query(self, node, left, right, from_idx, to_idx):
        if to_idx < left or right < from_idx:
            return float('inf')
        if from_idx <= left and right <= to_idx:
            return self.tree[node]
        mid = left + (right - left) // 2
        leftdir = self.query(2 * node + 1, left, mid, from_idx, to_idx)
        rightdir = self.query(2 * node + 2, mid + 1, right, from_idx, to_idx)
        return min(leftdir, rightdir)
```

## 6. C++ Solution

### Required Concepts

- Vectors
- Recursion
- Segment Trees

### AI-Generated C++ Implementation

```cpp
#include <vector>
#include <algorithm>
#include <climits>

class Solution {
public:
    std::vector<int> tree;

    void buildTree(const std::vector<int>& arr, int node, int left, int right) {
        if (left == right) {
            tree[node] = arr[left];
            return;
        }
        int mid = left + (right - left) / 2;
        buildTree(arr, 2 * node + 1, left, mid);
        buildTree(arr, 2 * node + 2, mid + 1, right);
        tree[node] = std::min(tree[2 * node + 1], tree[2 * node + 2]);
    }

    int query(int node, int left, int right, int from, int to) {
        if (to < left || right < from) {
            return INT_MAX;
        }
        if (from <= left && right <= to) {
            return tree[node];
        }
        int mid = left + (right - left) / 2;
        int leftdir = query(2 * node + 1, left, mid, from, to);
        int rightdir = query(2 * node + 2, mid + 1, right, from, to);
        return std::min(leftdir, rightdir);
    }
};
```

## 7. Rust Solution

### Required Concepts

- Vectors
- Recursion
- Borrowing

### AI-Generated Rust Implementation

```rust
pub struct Solution {
    tree: Vec<i32>,
}

impl Solution {
    pub fn new(arr: &[i32]) -> Self {
        let n = arr.len();
        let mut sol = Solution {
            tree: vec![0; 4 * n],
        };
        sol.build_tree(arr, 0, 0, n as i32 - 1);
        sol
    }

    fn build_tree(&mut self, arr: &[i32], node: usize, left: i32, right: i32) {
        if left == right {
            self.tree[node] = arr[left as usize];
            return;
        }
        let mid = left + (right - left) / 2;
        self.build_tree(arr, 2 * node + 1, left, mid);
        self.build_tree(arr, 2 * node + 2, mid + 1, right);
        self.tree[node] = std::cmp::min(self.tree[2 * node + 1], self.tree[2 * node + 2]);
    }

    pub fn query(&self, node: usize, left: i32, right: i32, from: i32, to: i32) -> i32 {
        if to < left || right < from {
            return i32::MAX;
        }
        if from <= left && right <= to {
            return self.tree[node];
        }
        let mid = left + (right - left) / 2;
        let leftdir = self.query(2 * node + 1, left, mid, from, to);
        let rightdir = self.query(2 * node + 2, mid + 1, right, from, to);
        std::cmp::min(leftdir, rightdir)
    }
}
```

## 8. Motivation

> "Mastering complex data structures like segment trees turns seemingly intractable range problems into elegant logarithmic triumphs."

<div align="center">

## Thank You 🚀

</div>
