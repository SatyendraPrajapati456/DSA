# Range Min Max Queries

## 1. Problem Details

**Platform:** GeeksforGeeks

**Question Link:**
https://www.geeksforgeeks.org/problems/range-min-max-queries4557/1

**Question Name:** Range Min Max Queries

**Question Description:**

Refer to GeeksforGeeks problem statement.

## 2. Test Cases

### Test Case 1: Standard Example

Input:
```text
arr = [1, 3, 2, 7, 9, 11], queries = [[1, 1, 4], [2, 3, 6], [1, 1, 4]]
```

Output:
```text
[[2, 9], [2, 6]]
```

Explanation:
Query 1 asks for min/max in range [1, 4] which gives min=2, max=9. Update query 2 changes index 3 to 6. Query 3 asks again for range [1, 4], updating the max/min results.

### Test Case 2: Edge Case Single Element

Input:
```text
arr = [5], queries = [[1, 0, 0], [2, 0, 10], [1, 0, 0]]
```

Output:
```text
[[5, 5], [10, 10]]
```

Explanation:
Single element array correctly handles queries and updates.

### Test Case 3: Constraint Boundary

Input:
```text
arr = [10, 20, 30, 40], queries = [[1, 0, 3]]
```

Output:
```text
[[10, 40]]
```

Explanation:
Query spanning the entire array returns the absolute minimum and maximum.

## 3. AI-Generated Approach

### Approach: Segment Tree

Use two separate segment trees—one for range minimum queries and another for range maximum queries—to efficiently process both point updates and range min/max queries in logarithmic time.

**Step-by-Step Reasoning:**
1. Initialize two segment trees, mintree and maxtree, each of size 4*n to store minimums and maximums respectively.
2. Build both segment trees recursively from the initial array in O(n) time.
3. Process each query: if type is 1, query the range [l, r] on both trees and store the results; if type is 2, update the value at the given index in both trees in O(log n) time.

**Why It Works:**
Segment trees divide the array into hierarchical segments, allowing range queries and point updates to be handled by visiting at most O(log n) nodes per operation instead of scanning linearly.

### Time Complexity

O(Q log N)

### Space Complexity

O(N)

## 4. Java Solution

### Required Concepts

- Segment Tree
- Recursion
- Range Queries

### Original Accepted Submission

```java
import java.util.*;

class Solution {
    int[] maxtree;
    int[] mintree;
    int n;

    public ArrayList<ArrayList<Integer>> rangeMinMaxQueries(
            int[] arr, int[][] queries) {

        n = arr.length;
        mintree = new int[4 * n];
        maxtree = new int[4 * n];

        minbuild(arr, 0, 0, n - 1);
        maxbuild(arr, 0, 0, n - 1);

        ArrayList<ArrayList<Integer>> ans = new ArrayList<>();

        for (int[] query : queries) {
            int type = query[0];

            if (type == 1) {
                int l = query[1];
                int r = query[2];

                ArrayList<Integer> temp = new ArrayList<>();
                temp.add(minquery(0, 0, n - 1, l, r));
                temp.add(maxquery(0, 0, n - 1, l, r));

                ans.add(temp);
            } else if (type == 2) {
                int index = query[1];
                int value = query[2];

                update(0, 0, n - 1, index, value);
            }
        }
```

### AI-Generated Java Alternative

```java
import java.util.*;

class Solution {
    int[] maxtree;
    int[] mintree;
    int n;

    private void minbuild(int[] arr, int node, int start, int end) {
        if (start == end) {
            mintree[node] = arr[start];
            return;
        }
        int mid = (start + end) / 2;
        minbuild(arr, 2 * node + 1, start, mid);
        minbuild(arr, 2 * node + 2, mid + 1, end);
        mintree[node] = Math.min(mintree[2 * node + 1], mintree[2 * node + 2]);
    }

    private void maxbuild(int[] arr, int node, int start, int end) {
        if (start == end) {
            maxtree[node] = arr[start];
            return;
        }
        int mid = (start + end) / 2;
        maxbuild(arr, 2 * node + 1, start, mid);
        maxbuild(arr, 2 * node + 2, mid + 1, end);
        maxtree[node] = Math.max(maxtree[2 * node + 1], maxtree[2 * node + 2]);
    }

    private int minquery(int node, int start, int end, int l, int r) {
        if (r < start || end < l) return Integer.MAX_VALUE;
        if (l <= start && end <= r) return mintree[node];
        int mid = (start + end) / 2;
        int p1 = minquery(2 * node + 1, start, mid, l, r);
        int p2 = minquery(2 * node + 2, mid + 1, end, l, r);
        return Math.min(p1, p2);
    }

    private int maxquery(int node, int start, int end, int l, int r) {
        if (r < start || end < l) return Integer.MIN_VALUE;
        if (l <= start && end <= r) return maxtree[node];
        int mid = (start + end) / 2;
        int p1 = maxquery(2 * node + 1, start, mid, l, r);
        int p2 = maxquery(2 * node + 2, mid + 1, end, l, r);
        return Math.max(p1, p2);
    }

    private void update(int node, int start, int end, int idx, int val) {
        if (start == end) {
            mintree[node] = val;
            maxtree[node] = val;
            return;
        }
        int mid = (start + end) / 2;
        if (idx <= mid) {
            update(2 * node + 1, start, mid, idx, val);
        } else {
            update(2 * node + 2, mid + 1, end, idx, val);
        }
        mintree[node] = Math.min(mintree[2 * node + 1], mintree[2 * node + 2]);
        maxtree[node] = Math.max(maxtree[2 * node + 1], maxtree[2 * node + 2]);
    }

    public ArrayList<ArrayList<Integer>> rangeMinMaxQueries(
            int[] arr, int[][] queries) {
        n = arr.length;
        mintree = new int[4 * n];
        maxtree = new int[4 * n];

        minbuild(arr, 0, 0, n - 1);
        maxbuild(arr, 0, 0, n - 1);

        ArrayList<ArrayList<Integer>> ans = new ArrayList<>();

        for (int[] query : queries) {
            int type = query[0];
            if (type == 1) {
                int l = query[1];
                int r = query[2];
                ArrayList<Integer> temp = new ArrayList<>();
                temp.add(minquery(0, 0, n - 1, l, r));
                temp.add(maxquery(0, 0, n - 1, l, r));
                ans.add(temp);
            } else if (type == 2) {
                int index = query[1];
                int value = query[2];
                update(0, 0, n - 1, index, value);
            }
        }
        return ans;
    }
}
```

## 5. Python Solution

### Required Concepts

- Lists
- Recursion
- Segment Tree

### AI-Generated Python Implementation

```python
class Solution:
    def rangeMinMaxQueries(self, arr: list[int], queries: list[list[int]]) -> list[list[int]]:
        n = len(arr)
        mintree = [0] * (4 * n)
        maxtree = [0] * (4 * n)
        
        def minbuild(node, start, end):
            if start == end:
                mintree[node] = arr[start]
                return
            mid = (start + end) // 2
            minbuild(2 * node + 1, start, mid)
            minbuild(2 * node + 2, mid + 1, end)
            mintree[node] = min(mintree[2 * node + 1], mintree[2 * node + 2])
            
        def maxbuild(node, start, end):
            if start == end:
                maxtree[node] = arr[start]
                return
            mid = (start + end) // 2
            maxbuild(2 * node + 1, start, mid)
            maxbuild(2 * node + 2, mid + 1, end)
            maxtree[node] = max(maxtree[2 * node + 1], maxtree[2 * node + 2])
            
        def minquery(node, start, end, l, r):
            if r < start or end < l:
                return float('inf')
            if l <= start and end <= r:
                return mintree[node]
            mid = (start + end) // 2
            return min(minquery(2 * node + 1, start, mid, l, r), minquery(2 * node + 2, mid + 1, end, l, r))
            
        def maxquery(node, start, end, l, r):
            if r < start or end < l:
                return float('-inf')
            if l <= start and end <= r:
                return maxtree[node]
            mid = (start + end) // 2
            return max(maxquery(2 * node + 1, start, mid, l, r), maxquery(2 * node + 2, mid + 1, end, l, r))
            
        def update(node, start, end, idx, val):
            if start == end:
                mintree[node] = val
                maxtree[node] = val
                return
            mid = (start + end) // 2
            if idx <= mid:
                update(2 * node + 1, start, mid, idx, val)
            else:
                update(2 * node + 2, mid + 1, end, idx, val)
            mintree[node] = min(mintree[2 * node + 1], mintree[2 * node + 2])
            maxtree[node] = max(maxtree[2 * node + 1], maxtree[2 * node + 2])
            
        minbuild(0, 0, n - 1)
        maxbuild(0, 0, n - 1)
        
        ans = []
        for q in queries:
            if q[0] == 1:
                ans.append([minquery(0, 0, n - 1, q[1], q[2]), maxquery(0, 0, n - 1, q[1], q[2])])
            elif q[0] == 2:
                update(0, 0, n - 1, q[1], q[2])
        return ans
```

## 6. C++ Solution

### Required Concepts

- std::vector
- Segment Tree
- References

### AI-Generated C++ Implementation

```cpp
#include <vector>
#include <algorithm>
#include <climits>

using namespace std;

class Solution {
    vector<int> mintree;
    vector<int> maxtree;
    int n;

    void minbuild(const vector<int>& arr, int node, int start, int end) {
        if (start == end) {
            mintree[node] = arr[start];
            return;
        }
        int mid = (start + end) / 2;
        minbuild(arr, 2 * node + 1, start, mid);
        minbuild(arr, 2 * node + 2, mid + 1, end);
        mintree[node] = min(mintree[2 * node + 1], mintree[2 * node + 2]);
    }

    void maxbuild(const vector<int>& arr, int node, int start, int end) {
        if (start == end) {
            maxtree[node] = arr[start];
            return;
        }
        int mid = (start + end) / 2;
        maxbuild(arr, 2 * node + 1, start, mid);
        maxbuild(arr, 2 * node + 2, mid + 1, end);
        maxtree[node] = max(maxtree[2 * node + 1], maxtree[2 * node + 2]);
    }

    int minquery(int node, int start, int end, int l, int r) {
        if (r < start || end < l) return INT_MAX;
        if (l <= start && end <= r) return mintree[node];
        int mid = (start + end) / 2;
        return min(minquery(2 * node + 1, start, mid, l, r), minquery(2 * node + 2, mid + 1, end, l, r));
    }

    int maxquery(int node, int start, int end, int l, int r) {
        if (r < start || end < l) return INT_MIN;
        if (l <= start && end <= r) return maxtree[node];
        int mid = (start + end) / 2;
        return max(maxquery(2 * node + 1, start, mid, l, r), maxquery(2 * node + 2, mid + 1, end, l, r));
    }

    void update(int node, int start, int end, int idx, int val) {
        if (start == end) {
            mintree[node] = val;
            maxtree[node] = val;
            return;
        }
        int mid = (start + end) / 2;
        if (idx <= mid) {
            update(2 * node + 1, start, mid, idx, val);
        } else {
            update(2 * node + 2, mid + 1, end, idx, val);
        }
        mintree[node] = min(mintree[2 * node + 1], mintree[2 * node + 2]);
        maxtree[node] = max(maxtree[2 * node + 1], maxtree[2 * node + 2]);
    }

public:
    vector<vector<int>> rangeMinMaxQueries(vector<int>& arr, vector<vector<int>>& queries) {
        n = arr.size();
        mintree.assign(4 * n, 0);
        maxtree.assign(4 * n, 0);

        minbuild(arr, 0, 0, n - 1);
        maxbuild(arr, 0, 0, n - 1);

        vector<vector<int>> ans;
        for (const auto& q : queries) {
            if (q[0] == 1) {
                ans.push_back({minquery(0, 0, n - 1, q[1], q[2]), maxquery(0, 0, n - 1, q[1], q[2])});
            } else if (q[0] == 2) {
                update(0, 0, n - 1, q[1], q[2]);
            }
        }
        return ans;
    }
};
```

## 7. Rust Solution

### Required Concepts

- Vec
- Recursion
- Mutability

### AI-Generated Rust Implementation

```rust
impl Solution {
    pub fn range_min_max_queries(arr: Vec<i32>, queries: Vec<Vec<i32>>) -> Vec<Vec<i32>> {
        let n = arr.len();
        let mut mintree = vec![0; 4 * n];
        let mut maxtree = vec![0; 4 * n];

        fn minbuild(arr: &Vec<i32>, mintree: &mut Vec<i32>, node: usize, start: usize, end: usize) {
            if start == end {
                mintree[node] = arr[start];
                return;
            }
            let mid = (start + end) / 2;
            minbuild(arr, mintree, 2 * node + 1, start, mid);
            minbuild(arr, mintree, 2 * node + 2, mid + 1, end);
            mintree[node] = std::cmp::min(mintree[2 * node + 1], mintree[2 * node + 2]);
        }

        fn maxbuild(arr: &Vec<i32>, maxtree: &mut Vec<i32>, node: usize, start: usize, end: usize) {
            if start == end {
                maxtree[node] = arr[start];
                return;
            }
            let mid = (start + end) / 2;
            maxbuild(arr, maxtree, 2 * node + 1, start, mid);
            maxbuild(arr, maxtree, 2 * node + 2, mid + 1, end);
            maxtree[node] = std::cmp::max(maxtree[2 * node + 1], maxtree[2 * node + 2]);
        }

        fn minquery(mintree: &Vec<i32>, node: usize, start: usize, end: usize, l: usize, r: usize) -> i32 {
            if r < start || end < l {
                return i32::MAX;
            }
            if l <= start && end <= r {
                return mintree[node];
            }
            let mid = (start + end) / 2;
            std::cmp::min(
                minquery(mintree, 2 * node + 1, start, mid, l, r),
                minquery(mintree, 2 * node + 2, mid + 1, end, l, r),
            )
        }

        fn maxquery(maxtree: &Vec<i32>, node: usize, start: usize, end: usize, l: usize, r: usize) -> i32 {
            if r < start || end < l {
                return i32::MIN;
            }
            if l <= start && end <= r {
                return maxtree[node];
            }
            let mid = (start + end) / 2;
            std::cmp::max(
                maxquery(maxtree, 2 * node + 1, start, mid, l, r),
                maxquery(maxtree, 2 * node + 2, mid + 1, end, l, r),
            )
        }

        fn update(mintree: &mut Vec<i32>, maxtree: &mut Vec<i32>, node: usize, start: usize, end: usize, idx: usize, val: i32) {
            if start == end {
                mintree[node] = val;
                maxtree[node] = val;
                return;
            }
            let mid = (start + end) / 2;
            if idx <= mid {
                update(mintree, maxtree, 2 * node + 1, start, mid, idx, val);
            } else {
                update(mintree, maxtree, 2 * node + 2, mid + 1, end, idx, val);
            }
            mintree[node] = std::cmp::min(mintree[2 * node + 1], mintree[2 * node + 2]);
            maxtree[node] = std::cmp::max(maxtree[2 * node + 1], maxtree[2 * node + 2]);
        }

        minbuild(&arr, &mut mintree, 0, 0, n - 1);
        maxbuild(&arr, &mut maxtree, 0, 0, n - 1);

        let mut ans = Vec::new();
        for q in queries {
            if q[0] == 1 {
                let l = q[1] as usize;
                let r = q[2] as usize;
                let min_val = minquery(&mintree, 0, 0, n - 1, l, r);
                let max_val = maxquery(&maxtree, 0, 0, n - 1, l, r);
                ans.push(vec![min_val, max_val]);
            } else if q[0] == 2 {
                let idx = q[1] as usize;
                let val = q[2];
                update(&mut mintree, &mut maxtree, 0, 0, n - 1, idx, val);
            }
        }
        ans
    }
}
```

## 8. Motivation

> "Excellence is not an act, but a habit. Keep practicing and refining your data structure intuition."

<div align="center">

## Thank You 🚀

</div>
