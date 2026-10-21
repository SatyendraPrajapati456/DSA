# Two Sum

## 1. Problem Details

**Platform:** LeetCode

**Question Link:**
https://leetcode.com/problems/two-sum

**Question Name:** Two Sum

**Question Description:**

Refer to LeetCode problem description.

## 2. Test Cases

### Test Case 1: Standard Example

Input:
```text
nums = [2, 7, 11, 15], target = 9
```

Output:
```text
[0, 1]
```

Explanation:
nums[0] + nums[1] == 2 + 7 = 9, so indices 0 and 1 are returned.

### Test Case 2: Duplicate Values

Input:
```text
nums = [3, 3], target = 6
```

Output:
```text
[0, 1]
```

Explanation:
nums[0] + nums[1] == 3 + 3 = 6, returning indices 0 and 1.

### Test Case 3: Negative Numbers

Input:
```text
nums = [-3, 4, 3, 90], target = 0
```

Output:
```text
[0, 2]
```

Explanation:
nums[0] + nums[2] == -3 + 3 = 0, returning indices 0 and 2.

## 3. AI-Generated Approach

### Approach: Brute Force (Nested Loops)

Exhaustively check every possible pair of elements in the array to find two numbers whose sum equals the given target value.

**Step-by-Step Reasoning:**
1. Iterate through the array with an outer loop variable 'i' from index 0 up to n - 1.
2. Iterate through the remaining elements with an inner loop variable 'j' starting from i + 1 up to n - 1 to avoid duplicate or self-pair checks.
3. Check if nums[i] + nums[j] equals target. If a match is found, immediately return an array containing the indices [i, j].
4. If no matching pair is found after inspecting all pairs, return default fallback indices [-1, -1].

**Why It Works:**
By examining every pair of distinct indices (i, j) where i < j, the algorithm guarantees that if a valid pair exists, it will be evaluated and identified.

### Time Complexity

O(n²)

### Space Complexity

O(1)

## 4. Java Solution

### Required Concepts

- Arrays
- Nested Loops
- Array Indexing

### Original Accepted Submission

```java
1class Solution {
2    public int[] twoSum(int[] nums, int target) {
3        int n = nums.length;
4        for (int i = 0; i < n; i++) {
5            for (int j = i + 1; j < n; j++) {
6                if ((nums[i] + nums[j]) == target) {
7                    return new int[] { i, j };
8                }
9            }
10        }
11        return new int []{-1,-1};
12    }
13}
```

### AI-Generated Java Alternative

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int n = nums.length;
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                if ((nums[i] + nums[j]) == target) {
                    return new int[] { i, j };
                }
            }
        }
        return new int[] { -1, -1 };
    }
}
```

## 5. Python Solution

### Required Concepts

- Lists
- Range Indexing
- Nested Loops

### AI-Generated Python Implementation

```python
class Solution:
    def twoSum(self, nums: list[int], target: int) -> list[int]:
        n = len(nums)
        for i in range(n):
            for j in range(i + 1, n):
                if nums[i] + nums[j] == target:
                    return [i, j]
        return [-1, -1]
```

## 6. C++ Solution

### Required Concepts

- std::vector
- Pass-by-reference
- Nested Iteration

### AI-Generated C++ Implementation

```cpp
#include <vector>

class Solution {
public:
    std::vector<int> twoSum(std::vector<int>& nums, int target) {
        int n = nums.size();
        for (int i = 0; i < n; ++i) {
            for (int j = i + 1; j < n; ++j) {
                if (nums[i] + nums[j] == target) {
                    return {i, j};
                }
            }
        }
        return {-1, -1};
    }
};
```

## 7. Rust Solution

### Required Concepts

- Vec
- Ranges
- Type Casting (as i32)

### AI-Generated Rust Implementation

```rust
impl Solution {
    pub fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
        let n = nums.len();
        for i in 0..n {
            for j in (i + 1)..n {
                if nums[i] + nums[j] == target {
                    return vec![i as i32, j as i32];
                }
            }
        }
        vec![-1, -1]
    }
}
```

## 8. Motivation

> "Mastery begins with understanding every solution completely, from brute force to optimal, building intuition step by step."

<div align="center">

## Thank You 🚀

</div>
