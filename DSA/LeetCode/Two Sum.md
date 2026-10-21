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
nums = [2, 7, 11, 15], target = 9
```

Output:
```text
[0, 1]
```

Explanation:
nums[0] + nums[1] == 2 + 7 == 9, so [0, 1] is returned.

### Test Case 2: Duplicate Elements

Input:
```text
nums = [3, 3], target = 6
```

Output:
```text
[0, 1]
```

Explanation:
The pair consists of two duplicate numbers with distinct indices: nums[0] (3) and nums[1] (3).

### Test Case 3: Negative Numbers

Input:
```text
nums = [-1, -2, -3, -4, -5], target = -8
```

Output:
```text
[2, 4]
```

Explanation:
nums[2] + nums[4] == -3 + (-5) == -8, so [2, 4] is returned.

## 3. AI-Generated Approach

### Approach: One-pass Hash Map

Iterate through the array while maintaining a hash map that maps numbers to their indices. For each element, check whether its complement (target - num) has already been seen in the map.

**Step-by-Step Reasoning:**
1. Initialize an empty hash map 'seen' to store value-to-index associations.
2. Iterate over the array with index 'i' and value 'num'.
3. Compute the complement: comp = target - num.
4. If 'comp' is present in 'seen', return the pair of indices [seen[comp], i].
5. Otherwise, insert 'num' into 'seen' with index 'i' and continue.
6. Return an empty collection if no pair is found (though guaranteed by constraints to have one).

**Why It Works:**
Because addition is commutative (a + b = target is equivalent to b = target - a), when we reach the second element of the complement pair, the first element has already been visited and stored in the hash map. Looking up the complement takes O(1) average time, reducing the brute-force O(n^2) search to O(n).

### Time Complexity

O(n)

### Space Complexity

O(n)

## 4. Java Solution

### Required Concepts

- HashMap lookup and insertion
- Autoboxing / Unboxing
- One-pass traversal

### AI-Generated Java Implementation

```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> seen = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int comp = target - nums[i];
            if (seen.containsKey(comp)) {
                return new int[] { seen.get(comp), i };
            }
            seen.put(nums[i], i);
        }
        return new int[] {};
    }
}
```

## 5. Python Solution

### Required Concepts

- Dictionaries (hash tables)
- enumerate
- Complement arithmetic

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
from typing import List

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

## 6. C++ Solution

### Required Concepts

- std::unordered_map
- Iterator find vs end()
- Vector initialization

### AI-Generated C++ Implementation

```cpp
#include <vector>
#include <unordered_map>

class Solution {
public:
    std::vector<int> twoSum(std::vector<int>& nums, int target) {
        std::unordered_map<int, int> seen;
        for (int i = 0; i < static_cast<int>(nums.size()); ++i) {
            int comp = target - nums[i];
            auto it = seen.find(comp);
            if (it != seen.end()) {
                return {it->second, i};
            }
            seen[nums[i]] = i;
        }
        return {};
    }
};
```

## 7. Rust Solution

### Required Concepts

- HashMap::get and Pattern Matching
- Ownership and Borrowing
- Type Casting (as i32)

### AI-Generated Rust Implementation

```rust
use std::collections::HashMap;

impl Solution {
    pub fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
        let mut seen = HashMap::new();
        for (i, &num) in nums.iter().enumerate() {
            let comp = target - num;
            if let Some(&prev_idx) = seen.get(&comp) {
                return vec![prev_idx as i32, i as i32];
            }
            seen.insert(num, i);
        }
        vec![]
    }
}
```

## 8. Motivation

> "Simplicity is prerequisite for reliability. Transforming an O(n^2) brute force into an elegant O(n) hash map solution is the foundational milestone of algorithmic thinking."

<div align="center">

## Thank You 🚀

</div>
