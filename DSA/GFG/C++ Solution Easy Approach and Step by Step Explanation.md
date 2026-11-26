# C++ Solution  ||  Easy Approach and Step by Step Explanation

## 1. Problem Details

**Platform:** GeeksforGeeks

**Question Link:**
https://www.geeksforgeeks.org/problems/range-vowel-count-queries-static/1

**Question Name:** C++ Solution  ||  Easy Approach and Step by Step Explanation

**Question Description:**

Refer to GeeksforGeeks problem statement.

## 2. Test Cases

### Test Case 1: Standard Vowel Query

Input:
```text
str = "geeksforgeeks", queries = [[0, 5]]
```

Output:
```text
3
```

Explanation:
In the substring "geeksf", vowels are 'e', 'e', 'e' which gives a total count of 3.

### Test Case 2: No Vowels

Input:
```text
str = "bcdfg", queries = [[0, 4]]
```

Output:
```text
0
```

Explanation:
The substring "bcdfg" contains no vowels.

### Test Case 3: Single Character Query

Input:
```text
str = "a", queries = [[0, 0]]
```

Output:
```text
1
```

Explanation:
The single character 'a' is a vowel.

## 3. AI-Generated Approach

### Approach: Segment Tree

Use a Segment Tree to efficiently answer range vowel count queries in logarithmic time per query.

**Step-by-Step Reasoning:**
1. Check if a character is a vowel ('a', 'e', 'i', 'o', 'u').
2. Build the segment tree where each node stores the count of vowels in its corresponding range.
3. For each query [l, r], traverse the segment tree to sum up vowel counts for completely or partially overlapping intervals.

**Why It Works:**
Segment tree divides the range into intervals of power of two sizes, allowing range query processing in O(log N) time instead of O(N) linear scans.

### Time Complexity

O(N log N) for tree construction and O(log N) per query

### Space Complexity

O(N)

## 4. Java Solution

### Required Concepts

- Segment Tree
- Recursion
- Range Queries

### Original Accepted Submission

```java
int mid = (start + end) / 2;

        // Build left subtree
        buildtree(s, 2 * node + 1, start, mid);

        // Build right subtree
        buildtree(s, 2 * node + 2, mid + 1, end);

        // Merge both children
        tree[node] = tree[2 * node + 1] +
                     tree[2 * node + 2];
    }

    // Query range [l, r]
    int query(int node, int start, int end, int l, int r) {

        // No overlap
        if (start > r || end < l) {
            return 0;
        }

        // Complete overlap
        if (start >= l && end <= r) {
            return tree[node];
        }

        // Partial overlap
        int mid = (start + end) / 2;

        int left = query(2 * node + 1, start, mid, l, r);

        int right = query(2 * node + 2, mid + 1, end, l, r);

        return left + right;
    }
}
```

### AI-Generated Java Alternative

```java
import java.util.*;

class Solution {
    static int[] tree;
    
    static boolean isVowel(char c) {
        return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u' ||
               c == 'A' || c == 'E' || c == 'I' || c == 'O' || c == 'U';
    }
    
    static void buildtree(String s, int node, int start, int end) {
        if (start == end) {
            tree[node] = isVowel(s.charAt(start)) ? 1 : 0;
            return;
        }
        int mid = (start + end) / 2;
        buildtree(s, 2 * node + 1, start, mid);
        buildtree(s, 2 * node + 2, mid + 1, end);
        tree[node] = tree[2 * node + 1] + tree[2 * node + 2];
    }

    static int query(int node, int start, int end, int l, int r) {
        if (start > r || end < l) {
            return 0;
        }
        if (start >= l && end <= r) {
            return tree[node];
        }
        int mid = (start + end) / 2;
        int left = query(2 * node + 1, start, mid, l, r);
        int right = query(2 * node + 2, mid + 1, end, l, r);
        return left + right;
    }
    
    public static int[] rangeVowelQuery(String s, int[][] queries) {
        int n = s.length();
        tree = new int[4 * n];
        buildtree(s, 0, 0, n - 1);
        int[] ans = new int[queries.length];
        for (int i = 0; i < queries.length; i++) {
            ans[i] = query(0, 0, n - 1, queries[i][0], queries[i][1]);
        }
        return ans;
    }
}
```

## 5. Python Solution

### Required Concepts

- Recursion
- Segment Tree
- Range Sum

### AI-Generated Python Implementation

```python
class Solution:
    def rangeVowelQuery(self, s: str, queries: list[list[int]]) -> list[int]:
        n = len(s)
        tree = [0] * (4 * n)
        
        def is_vowel(c):
            return c in "aeiouAEIOU"
            
        def build(node, start, end):
            if start == end:
                tree[node] = 1 if is_vowel(s[start]) else 0
                return
            mid = (start + end) // 2
            build(2 * node + 1, start, mid)
            build(2 * node + 2, mid + 1, end)
            tree[node] = tree[2 * node + 1] + tree[2 * node + 2]
            
        def query(node, start, end, l, r):
            if start > r or end < l:
                return 0
            if start >= l and end <= r:
                return tree[node]
            mid = (start + end) // 2
            left = query(2 * node + 1, start, mid, l, r)
            right = query(2 * node + 2, mid + 1, end, l, r)
            return left + right
            
        build(0, 0, n - 1)
        return [query(0, 0, n - 1, q[0], q[1]) for q in queries]
```

## 6. C++ Solution

### Required Concepts

- Vectors
- Segment Tree
- Recursion

### AI-Generated C++ Implementation

```cpp
#include <bits/stdc++.h>
using namespace std;

class Solution {
    vector<int> tree;
    bool isVowel(char c) {
        return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u' ||
               c == 'A' || c == 'E' || c == 'I' || c == 'O' || c == 'U';
    }
    void buildtree(const string& s, int node, int start, int end) {
        if (start == end) {
            tree[node] = isVowel(s[start]) ? 1 : 0;
            return;
        }
        int mid = (start + end) / 2;
        buildtree(s, 2 * node + 1, start, mid);
        buildtree(s, 2 * node + 2, mid + 1, end);
        tree[node] = tree[2 * node + 1] + tree[2 * node + 2];
    }
    int query(int node, int start, int end, int l, int r) {
        if (start > r || end < l) return 0;
        if (start >= l && end <= r) return tree[node];
        int mid = (start + end) / 2;
        int left = query(2 * node + 1, start, mid, l, r);
        int right = query(2 * node + 2, mid + 1, end, l, r);
        return left + right;
    }
public:
    vector<int> rangeVowelQuery(string s, vector<vector<int>>& queries) {
        int n = s.length();
        tree.assign(4 * n, 0);
        buildtree(s, 0, 0, n - 1);
        vector<int> ans;
        for (const auto& q : queries) {
            ans.push_back(query(0, 0, n - 1, q[0], q[1]));
        }
        return ans;
    }
};
```

## 7. Rust Solution

### Required Concepts

- Vectors
- Recursion
- Segment Tree

### AI-Generated Rust Implementation

```rust
impl Solution {
    pub fn range_vowel_query(s: String, queries: Vec<Vec<i32>>) -> Vec<i32> {
        let bytes = s.as_bytes();
        let n = bytes.len();
        let mut tree = vec![0; 4 * n];

        fn is_vowel(c: u8) -> bool {
            matches!(c, b'a' | b'e' | b'i' | b'o' | b'u' | b'A' | b'E' | b'I' | b'O' | b'U')
        }

        fn build(bytes: &[u8], tree: &mut Vec<i32>, node: usize, start: usize, end: usize) {
            if start == end {
                tree[node] = if is_vowel(bytes[start]) { 1 } else { 0 };
                return;
            }
            let mid = (start + end) / 2;
            build(bytes, tree, 2 * node + 1, start, mid);
            build(bytes, tree, 2 * node + 2, mid + 1, end);
            tree[node] = tree[2 * node + 1] + tree[2 * node + 2];
        }

        fn query(tree: &Vec<i32>, node: usize, start: usize, end: usize, l: usize, r: usize) -> i32 {
            if start > r || end < l {
                return 0;
            }
            if start >= l && end <= r {
                return tree[node];
            }
            let mid = (start + end) / 2;
            let left = query(tree, 2 * node + 1, start, mid, l, r);
            let right = query(tree, 2 * node + 2, mid + 1, end, l, r);
            left + right
        }

        if n > 0 {
            build(bytes, &mut tree, 0, 0, n - 1);
        }

        queries
            .iter()
            .map(|q| query(&tree, 0, 0, n - 1, q[0] as usize, q[1] as usize))
            .collect()
    }
}
```

## 8. Motivation

> "Excellence is not an act, but a habit. Keep pushing the boundaries of your algorithmic thinking."

<div align="center">

## Thank You 🚀

</div>
