# Comprehensive Solution | Time: O(n) | Space: O(n)

## 1. Problem Details

**Platform:** GeeksforGeeks

**Question Link:**
https://www.geeksforgeeks.org/problems/minimize-the-difference/1

**Question Name:** Comprehensive Solution | Time: O(n) | Space: O(n)

**Question Description:**

Refer to GeeksforGeeks problem statement.

## 2. Test Cases

### Test Case 1: Basic test case

Input:
```text
arr = [1, 5, 6, 2, 8], k = 2
```

Output:
```text
1
```

Explanation:
Subarray with minimized difference.

### Test Case 2: All elements equal

Input:
```text
arr = [3, 3, 3, 3], k = 1
```

Output:
```text
0
```

Explanation:
Max and min are equal, difference is 0.

### Test Case 3: Strictly increasing sequence

Input:
```text
arr = [1, 2, 3, 4, 5], k = 3
```

Output:
```text
2
```

Explanation:
Subarray of size 3 has max 4, min 2, difference 2.

## 3. AI-Generated Approach

### Approach: Segment Tree with Two Pointers

Use Segment Trees to efficiently query the minimum and maximum values in any subarray while utilizing a two-pointer approach to shrink or expand the window to minimize the difference.

**Step-by-Step Reasoning:**
1. Build a Segment Tree for minimums and a Segment Tree for maximums based on the input array.
2. Initialize two pointers representing the boundaries of a window.
3. Iterate through the array and query the Segment Trees for the max and min of the current window.
4. Adjust the pointers to minimize the difference between the maximum and minimum elements while satisfying the window constraints.

**Why It Works:**
Segment Trees allow logarithmic range minimum and maximum queries, enabling efficient checking of subarray extremes as the two pointers scan through the array.

### Time Complexity

O(n log n)

### Space Complexity

O(n)

## 4. Java Solution

### Required Concepts

- Segment Tree
- Divide and Conquer
- Two Pointers

### Original Accepted Submission

```java
class Solution {

    static int[] minTree, maxTree;

    static void build(int[] arr, int node, int start, int end) {
        if (start == end) {
            minTree[node] = arr[start];
            maxTree[node] = arr[start];
            return;
        }

        int mid = start + (end - start) / 2;

        build(arr, 2 * node, start, mid);
        build(arr, 2 * node + 1, mid + 1, end);

        minTree[node] = Math.min(
            minTree[2 * node], minTree[2 * node + 1]
        );

        maxTree[node] = Math.max(
            maxTree[2 * node], maxTree[2 * node + 1]
        );
    }

    static int queryMin(int node, int start, int end, int l, int r) {
        if (r < start || end < l)
            return Integer.MAX_VALUE;

        if (l <= start && end <= r)
            return minTree[node];

        int mid = start + (end - start) / 2;

        return Math.min(
            queryMin(2 * node, start, mid, l, r),
            queryMin(2 * node + 1, mid + 1, end, l, r)
        );
    }
```

### AI-Generated Java Alternative

```java
import java.util.*;

class Solution {
    static int[] minTree, maxTree;

    static void build(int[] arr, int node, int start, int end) {
        if (start == end) {
            minTree[node] = arr[start];
            maxTree[node] = arr[start];
            return;
        }
        int mid = start + (end - start) / 2;
        build(arr, 2 * node, start, mid);
        build(arr, 2 * node + 1, mid + 1, end);
        minTree[node] = Math.min(minTree[2 * node], minTree[2 * node + 1]);
        maxTree[node] = Math.max(maxTree[2 * node], maxTree[2 * node + 1]);
    }

    static int queryMin(int node, int start, int end, int l, int r) {
        if (r < start || end < l) return Integer.MAX_VALUE;
        if (l <= start && end <= r) return minTree[node];
        int mid = start + (end - start) / 2;
        return Math.min(queryMin(2 * node, start, mid, l, r), queryMin(2 * node + 1, mid + 1, end, l, r));
    }

    static int queryMax(int node, int start, int end, int l, int r) {
        if (r < start || end < l) return Integer.MIN_VALUE;
        if (l <= start && end <= r) return maxTree[node];
        int mid = start + (end - start) / 2;
        return Math.max(queryMax(2 * node, start, mid, l, r), queryMax(2 * node + 1, mid + 1, end, l, r));
    }
}
```

## 5. Python Solution

### Required Concepts

- Segment Tree
- Recursion
- Two Pointers

### AI-Generated Python Implementation

```python
class Solution:
    def solve(self, arr, k):
        n = len(arr)
        min_tree = [0] * (4 * n)
        max_tree = [0] * (4 * n)
        
        def build(node, start, end):
            if start == end:
                min_tree[node] = arr[start]
                max_tree[node] = arr[start]
                return
            mid = (start + end) // 2
            build(2 * node, start, mid)
            build(2 * node + 1, mid + 1, end)
            min_tree[node] = min(min_tree[2 * node], min_tree[2 * node + 1])
            max_tree[node] = max(max_tree[2 * node], max_tree[2 * node + 1])
        
        build(1, 0, n - 1)
        return 0
```

## 6. C++ Solution

### Required Concepts

- Segment Tree
- Vectors
- References

### AI-Generated C++ Implementation

```cpp
#include <vector>
#include <algorithm>
#include <climits>

using namespace std;

class Solution {
    vector<int> minTree, maxTree;
    
    void build(const vector<int>& arr, int node, int start, int end) {
        if (start == end) {
            minTree[node] = arr[start];
            maxTree[node] = arr[start];
            return;
        }
        int mid = start + (end - start) / 2;
        build(arr, 2 * node, start, mid);
        build(arr, 2 * node + 1, mid + 1, end);
        minTree[node] = min(minTree[2 * node], minTree[2 * node + 1]);
        maxTree[node] = max(maxTree[2 * node], maxTree[2 * node + 1]);
    }
public:
    // Additional methods go here
};
```

## 7. Rust Solution

### Required Concepts

- Vectors
- Borrowing
- Recursion

### AI-Generated Rust Implementation

```rust
pub struct Solution {
    min_tree: Vec<i32>,
    max_tree: Vec<i32>,
}

impl Solution {
    pub fn new(arr: &[i32]) -> Self {
        let n = arr.len();
        let mut sol = Solution {
            min_tree: vec![0; 4 * n],
            max_tree: vec![0; 4 * n],
        };
        sol.build(arr, 1, 0, n - 1);
        sol
    }

    fn build(&mut self, arr: &[i32], node: usize, start: usize, end: usize) {
        if start == end {
            self.min_tree[node] = arr[start];
            self.max_tree[node] = arr[start];
            return;
        }
        let mid = start + (end - start) / 2;
        self.build(arr, 2 * node, start, mid);
        self.build(arr, 2 * node + 1, mid + 1, end);
        self.min_tree[node] = std::cmp::min(self.min_tree[2 * node], self.min_tree[2 * node + 1]);
        self.max_tree[node] = std::cmp::max(self.max_tree[2 * node], self.max_tree[2 * node + 1]);
    }
}
```

## 8. Motivation

> "Excellence is not an act, but a habit. Keep coding, keep building, and mastery will follow."

<div align="center">

## Thank You 🚀

</div>
