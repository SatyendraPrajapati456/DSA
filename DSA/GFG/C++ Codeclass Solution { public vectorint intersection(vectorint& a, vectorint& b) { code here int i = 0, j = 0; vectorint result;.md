# C++ Code:class Solution {  public:    vector<int> intersection(vector<int>& a, vector<int>& b) {        // code here        int i = 0, j = 0;    vector<int> result;

## 1. Problem Details

**Platform:** GeeksforGeeks

**Question Link:**
https://www.geeksforgeeks.org/problems/intersection-of-two-sorted-arrays-with-duplicate-elements/1

**Question Name:** C++ Code:class Solution {  public:    vector<int> intersection(vector<int>& a, vector<int>& b) {        // code here        int i = 0, j = 0;    vector<int> result;

**Question Description:**

Refer to GeeksforGeeks problem statement.

## 2. Test Cases

### Test Case 1: Standard Example

Input:
```text
a = [1, 2, 2, 3, 4], b = [2, 2, 4, 6]
```

Output:
```text
[2, 4]
```

Explanation:
Common elements are 2 and 4, with duplicates correctly filtered out.

### Test Case 2: No Common Elements

Input:
```text
a = [1, 3, 5], b = [2, 4, 6]
```

Output:
```text
[]
```

Explanation:
There are no overlapping values between the two arrays.

### Test Case 3: All Elements Common

Input:
```text
a = [1, 1, 2], b = [1, 2, 2]
```

Output:
```text
[1, 2]
```

Explanation:
Intersection contains unique common elements 1 and 2.

## 3. AI-Generated Approach

### Approach: Two Pointers

Use two pointers to traverse both sorted arrays simultaneously, efficiently finding common elements while handling duplicates by skipping consecutive identical values.

**Step-by-Step Reasoning:**
1. Initialize two pointers, i and j, to 0 for arrays a and b respectively.
2. Traverse both arrays while i < a.length and j < b.length.
3. Skip duplicate elements in array a by checking if a[i] == a[i-1] and incrementing i.
4. Skip duplicate elements in array b by checking if b[j] == b[j-1] and incrementing j.
5. If a[i] == b[j], add the element to the result list and increment both i and j.
6. If a[i] < b[j], increment i; otherwise, increment j.

**Why It Works:**
Since both input arrays are sorted, advancing pointers based on their relative values ensures we never miss a potential intersection and correctly handle duplicate elements in linear time.

### Time Complexity

O(N + M)

### Space Complexity

O(1)

## 4. Java Solution

### Required Concepts

- Array Traversal
- Two Pointers
- Duplicate Skipping

### Original Accepted Submission

```java
class Solution {
    ArrayList<Integer> intersection(int[] a, int[] b) {
        ArrayList<Integer> ans = new ArrayList<>();
        
        int i = 0, j = 0;
        
        while (i < a.length && j < b.length) {
            
            // Skip duplicates in a
            if (i > 0 && a[i] == a[i - 1]) {
                i++;
                continue;
            }
            
            // Skip duplicates in b
            if (j > 0 && b[j] == b[j - 1]) {
                j++;
                continue;
            }
            
            if (a[i] == b[j]) {
                ans.add(a[i]);
                i++;
                j++;
            } 
            else if (a[i] < b[j]) {
                i++;
            } 
            else {
                j++;
            }
        }
        
        return ans;
    }
}
```

### AI-Generated Java Alternative

```java
import java.util.ArrayList;

class Solution {
    ArrayList<Integer> intersection(int[] a, int[] b) {
        ArrayList<Integer> ans = new ArrayList<>();
        int i = 0, j = 0;
        
        while (i < a.length && j < b.length) {
            if (i > 0 && a[i] == a[i - 1]) {
                i++;
                continue;
            }
            if (j > 0 && b[j] == b[j - 1]) {
                j++;
                continue;
            }
            
            if (a[i] == b[j]) {
                ans.add(a[i]);
                i++;
                j++;
            } else if (a[i] < b[j]) {
                i++;
            } else {
                j++;
            }
        }
        return ans;
    }
}
```

## 5. Python Solution

### Required Concepts

- Lists
- Indices
- Two Pointers

### AI-Generated Python Implementation

```python
class Solution:
    def intersection(self, a: list[int], b: list[int]) -> list[int]:
        ans = []
        i, j = 0, 0
        
        while i < len(a) and j < len(b):
            if i > 0 and a[i] == a[i - 1]:
                i += 1
                continue
            if j > 0 and b[j] == b[j - 1]:
                j += 1
                continue
                
            if a[i] == b[j]:
                ans.append(a[i])
                i += 1
                j += 1
            elif a[i] < b[j]:
                i += 1
            else:
                j += 1
                
        return ans
```

## 6. C++ Solution

### Required Concepts

- std::vector
- Pointers
- Sorted Arrays

### AI-Generated C++ Implementation

```cpp
#include <vector>

using namespace std;

class Solution {
public:
    vector<int> intersection(vector<int>& a, vector<int>& b) {
        vector<int>
 ans;
        int i = 0, j = 0;
        
        while (i < a.size() && j < b.size()) {
            if (i > 0 && a[i] == a[i - 1]) {
                i++;
                continue;
            }
            if (j > 0 && b[j] == b[j - 1]) {
                j++;
                continue;
            }
            
            if (a[i] == b[j]) {
                ans.push_back(a[i]);
                i++;
                j++;
            } else if (a[i] < b[j]) {
                i++;
            } else {
                j++;
            }
        }
        return ans;
    }
};
```

## 7. Rust Solution

### Required Concepts

- Vectors
- Borrowing
- Index Iteration

### AI-Generated Rust Implementation

```rust
impl Solution {
    pub fn intersection(a: Vec<i32>, b: Vec<i32>) -> Vec<i32> {
        let mut ans = Vec::new();
        let mut i = 0;
        let mut j = 0;
        
        while i < a.len() && j < b.len() {
            if i > 0 && a[i] == a[i - 1] {
                i += 1;
                continue;
            }
            if j > 0 && b[j] == b[j - 1] {
                j += 1;
                continue;
            }
            
            if a[i] == b[j] {
                ans.push(a[i]);
                i += 1;
                j += 1;
            } else if a[i] < b[j] {
                i += 1;
            } else {
                j += 1;
            }
        }
        
        ans
    }
}
```

## 8. Motivation

> "Excellence is not an act, but a habit. Consistent practice of algorithmic patterns builds intuitive problem-solving mastery."

<div align="center">

## Thank You 🚀

</div>
