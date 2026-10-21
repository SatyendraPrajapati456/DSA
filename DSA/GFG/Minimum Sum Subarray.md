# Minimum Sum Subarray

## 1. Problem Details

**Platform:** GeeksforGeeks

**Question Link:**
https://www.geeksforgeeks.org/problems/smallest-sum-contiguous-subarray/1

**Question Name:** Minimum Sum Subarray

**Question Description:**

Refer to GeeksforGeeks problem statement.

## 2. Test Cases

### Test Case 1: Standard Mixed Numbers

Input:
```text
arr = [3, -4, 2, -3, -1, 7, -5]
```

Output:
```text
-6
```

Explanation:
The contiguous subarray with the minimum sum is [-4, 2, -3, -1], which sums to -6.

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
Since all numbers are positive, the minimum subarray is the single element with the smallest value, which is 1.

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
All numbers are negative, so taking the entire array [-2, -3, -4, -1, -2] yields the minimum sum of -12.

## 3. AI-Generated Approach

### Approach: Kadane's Algorithm (Minimum Subarray Variant)

Adapt Kadane's algorithm to track the minimum contiguous subarray sum. At each element, decide whether to extend the previous minimum subarray or start a new subarray beginning at the current element.

**Step-by-Step Reasoning:**
1. Initialize 'currSum' and 'minSum' with the value of the first element, arr[0].
2. Iterate through the array from index 1 to the end.
3. At index i, update 'currSum' to be the minimum of arr[i] and (currSum + arr[i]).
4. Update 'minSum' to be the minimum of 'minSum' and 'currSum'.
5. Return 'minSum' after processing all elements.

**Why It Works:**
Optimal substructure holds: the minimum subarray sum ending at index i is either arr[i] itself (starting a new subarray) or arr[i] added to the minimum subarray sum ending at index i-1. By tracking this locally and updating a global minimum, we consider all possible contiguous subarrays in linear time.

### Time Complexity

O(n)

### Space Complexity

O(1)

## 4. Java Solution

### Required Concepts

- Dynamic Programming
- Kadane's Algorithm
- Math.min

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
- Kadane's Variant
- Linear Scan

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
- Kadane's Algorithm

### AI-Generated C++ Implementation

```cpp
#include <vector>
#include <algorithm>

class Solution {
public:
    int minSubarraySum(const std::vector<int>& arr) {
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

- Borrowing
- Iterator skipping
- std::cmp::min

### AI-Generated Rust Implementation

```rust
pub struct Solution;

impl Solution {
    pub fn min_subarray_sum(arr: &[i32]) -> i32 {
        let mut curr_sum = arr[0];
        let mut min_sum = arr[0];

        for &val in arr.iter().skip(1) {
            curr_sum = std::cmp::min(val, curr_sum + val);
            min_sum = std::cmp::min(min_sum, curr_sum);
        }

        min_sum
    }
}
```

## 8. Motivation

> "Symmetry in algorithms is powerful: reversing the objective of a classic algorithm like Kadane's reveals new solutions with the same elegance and efficiency."

<div align="center">

## Thank You 🚀

</div>
