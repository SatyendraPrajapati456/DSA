# Minimum Sum Subarray

## 1. Problem Details

**Platform:** GeeksforGeeks

**Question Link:**
https://www.geeksforgeeks.org/problems/smallest-sum-contiguous-subarray/1

**Question Name:** Minimum Sum Subarray

**Question Description:**

Refer to GeeksforGeeks problem statement.

## 2. Test Cases

### Test Case 1: Standard Mixed Positive and Negative Elements

Input:
```text
arr = [3, -4, 2, -3, -1, 7, -5]
```

Output:
```text
-6
```

Explanation:
The contiguous subarray [-4, 2, -3, -1] yields the minimum sum of -6.

### Test Case 2: All Positive Numbers

Input:
```text
arr = [2, 6, 8, 1, 4]
```

Output:
```text
1
```

Explanation:
When all numbers are positive, the smallest contiguous sum is simply the minimum single element, which is 1.

### Test Case 3: All Negative Numbers

Input:
```text
arr = [-2, -3, -4, -1, -2]
```

Output:
```text
-12
```

Explanation:
Since all numbers are negative, extending the subarray across all elements yields the overall minimum sum of -12.

## 3. AI-Generated Approach

### Approach: Kadane's Algorithm (Minimum Subarray Sum Variant)

Adapt Kadane's classic maximum subarray algorithm to find the minimum contiguous sum by maintaining the minimum ending at the current position.

**Step-by-Step Reasoning:**
1. Initialize both `currSum` and `minSum` with the first element of the array `arr[0]`.
2. Iterate through the array starting from the second element (index 1).
3. For each element `arr[i]`, update `currSum` to be the minimum of `arr[i]` and `currSum + arr[i]` (deciding whether to start a new subarray or extend the existing one).
4. Update `minSum` to be the minimum of `minSum` and `currSum`.
5. Return `minSum` after traversing all elements.

**Why It Works:**
At each index i, the minimum contiguous subarray ending at i either starts at i (just `arr[i]`) or extends the minimum contiguous subarray ending at i-1 (`currSum + arr[i]`). This optimal substructure property allows a single-pass DP approach without needing an auxiliary array.

### Time Complexity

O(n)

### Space Complexity

O(1)

## 4. Java Solution

### Required Concepts

- Dynamic Programming (Kadane's)
- In-place State Tracking
- Primitive operations

### Original Accepted Submission

```java
class Solution {
    int minSubarraySum(int[] arr) {
        int currSum = arr[0];
        int minSum = arr[0];

        for (int i = 1; i < arr.length; i++) {
            currSum = Math.min(arr[i], currSum + arr[i]);
            minSum = Math.min(minSum, currSum);
        }

        return minSum;
    }
}
```

## 5. Python Solution

### Required Concepts

- Dynamic Programming
- Built-in min()
- Slice iteration

### AI-Generated Python Implementation

```python
class Solution:
    def minSubarraySum(self, arr: list[int]) -> int:
        curr_sum = arr[0]
        min_sum = arr[0]

        for x in arr[1:]:
            curr_sum = min(x, curr_sum + x)
            min_sum = min(min_sum, curr_sum)

        return min_sum
```

## 6. C++ Solution

### Required Concepts

- std::vector
- std::min
- Cache Locality

### AI-Generated C++ Implementation

```cpp
#include <vector>
#include <algorithm>

class Solution {
public:
    int minSubarraySum(std::vector<int>& arr) {
        int currSum = arr[0];
        int minSum = arr[0];

        for (size_t i = 1; i < arr.size(); ++i) {
            currSum = std::min(arr[i], currSum + arr[i]);
            minSum = std::min(minSum, currSum);
        }

        return minSum;
    }
};
```

## 7. Rust Solution

### Required Concepts

- Iterators
- std::cmp::min
- Borrowing

### AI-Generated Rust Implementation

```rust
pub struct Solution;

impl Solution {
    pub fn min_subarray_sum(arr: &[i32]) -> i32 {
        let mut curr_sum = arr[0];
        let mut min_sum = arr[0];

        for &x in arr.iter().skip(1) {
            curr_sum = std::cmp::min(x, curr_sum + x);
            min_sum = std::cmp::min(min_sum, curr_sum);
        }

        min_sum
    }
}
```

## 8. Motivation

> "Simple, elegant algorithms are often duals of one another; understanding the essence of Kadane's algorithm turns a maximum problem into a minimum solution effortlessly."

<div align="center">

## Thank You 🚀

</div>
