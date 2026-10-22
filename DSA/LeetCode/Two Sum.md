# Two Sum

## 1. Problem Details

**Platform:** LeetCode

**Question Link:**
https://leetcode.com/problems/two-sum/

**Question Name:** Two Sum

**Question Description:**

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
Assume that each input has exactly one solution, and you may not use the same element twice.

## 2. Test Cases

### Test Case 1: Standard Example

Input:
```text
nums = [2,7,11,15], target = 9
```

Output:
```text
[0,1]
```

Explanation:
nums[0] + nums[1] = 2 + 7 = 9.

### Test Case 2: Duplicate Values

Input:
```text
nums = [3,3], target = 6
```

Output:
```text
[0,1]
```

Explanation:
The two 3s at indices 0 and 1 sum to 6.

### Test Case 3: Negative Numbers

Input:
```text
nums = [-1,-2,-3,-4,-5], target = -8
```

Output:
```text
[2,4]
```

Explanation:
-3 + -5 = -8.

## 3. AI-Generated Approach

### Approach: Hash Map (One-pass)

Use a hash map to store the value of each element as a key and its index as the value. For every element, calculate its complement (target - current_value) and check if it already exists in the map.

**Step-by-Step Reasoning:**
1. Initialize an empty hash map to store visited numbers and their indices.
2. Iterate through the array using a loop, tracking both the current index and the value.
3. Calculate the complement by subtracting the current value from the target.
4. Check if the complement exists in the hash map. If it does, return the index stored in the map and the current index.
5. If the complement is not found, add the current value and its index to the hash map and continue.

**Why It Works:**
Since we are looking for x + y = target, for any x, we are looking for y = target - x. A hash map provides O(1) average time complexity for lookups, allowing us to find the complement in a single pass rather than using a nested loop.

### Time Complexity

O(n)

### Space Complexity

O(n)

## 4. Java Solution

### Required Concepts

- HashMap
- Array Indexing
- Autoboxing

### AI-Generated Java Implementation

```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[] { map.get(complement), i };
            }
            map.put(nums[i], i);
        }
        return new int[] {};
    }
}
```

## 5. Python Solution

### Required Concepts

- Dictionaries
- Enumerate
- Hashing

### Original Accepted Submission

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        seen = {}
        for i, num in enumerate(nums):
            comp = target - num
            if comp in seen:
                return [seen[comp], i]
            seen[num] = i
        return []
```

### AI-Generated Python Alternative

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        seen = {}
        for i, num in enumerate(nums):
            complement = target - num
            if complement in seen:
                return [seen[complement], i]
            seen[num] = i
        return []
```

## 6. C++ Solution

### Required Concepts

- std::unordered_map
- std::vector
- Iterators

### AI-Generated C++ Implementation

```cpp
#include <vector>
#include <unordered_map>

class Solution {
public:
    std::vector<int> twoSum(std::vector<int>& nums, int target) {
        std::unordered_map<int, int> seen;
        for (int i = 0; i < nums.size(); ++i) {
            int complement = target - nums[i];
            if (seen.find(complement) != seen.end()) {
                return {seen[complement], i};
            }
            seen[nums[i]] = i;
        }
        return {};
    }
};
```

## 7. Rust Solution

### Required Concepts

- HashMap
- Ownership
- Type Casting

### AI-Generated Rust Implementation

```rust
use std::collections::HashMap;

impl Solution {
    pub fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
        let mut seen = HashMap::new();
        for (i, &num) in nums.iter().enumerate() {
            let complement = target - num;
            if let Some(&prev_idx) = seen.get(&complement) {
                return vec![prev_idx as i32, i as i32];
            }
            seen.insert(num, i);
        }
        vec![]
    }
}
```

## 8. Motivation

> "The most efficient solution often comes from changing how you view the data—turning a search problem into a lookup problem."

<div align="center">

## Thank You 🚀

</div>
