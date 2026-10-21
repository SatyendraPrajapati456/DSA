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
nums[0] + nums[1] == 2 + 7 == 9, so we return [0, 1].

### Test Case 2: Different Order Example

Input:
```text
nums = [3, 2, 4], target = 6
```

Output:
```text
[1, 2]
```

Explanation:
nums[1] + nums[2] == 2 + 4 == 6, so we return [1, 2].

### Test Case 3: Duplicate Numbers

Input:
```text
nums = [3, 3], target = 6
```

Output:
```text
[0, 1]
```

Explanation:
nums[0] + nums[1] == 3 + 3 == 6, so we return [0, 1].

## 3. AI-Generated Approach

### Approach: Hash Map

Use a hash map to store each number and its corresponding index as we iterate through the array. For each element, check if its complement (target - current number) already exists in the hash map.

**Step-by-Step Reasoning:**
1. Initialize an empty hash map called 'seen' to store numbers and their indices.
2. Iterate through the array 'nums' using an index 'i' and value 'num'.
3. Calculate the complement by subtracting 'num' from 'target'.
4. Check if the complement exists in the 'seen' hash map. If it does, return the index of the complement and the current index 'i'.
5. If the complement is not in the hash map, store the current number and its index in 'seen'.

**Why It Works:**
By checking for the complement in the hash map during the single-pass traversal, we can find the two numbers in O(1) average time per lookup. Since we look back at numbers we have already seen, we guarantee that we do not use the same element twice and find the unique solution efficiently.

### Time Complexity

O(n)

### Space Complexity

O(n)

## 4. Java Solution

### Required Concepts

- Arrays
- HashMap
- Time Complexity

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
        return new int[0];
    }
}
```

## 5. Python Solution

### Required Concepts

- Lists
- Dictionaries
- In-place modification

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

## 6. C++ Solution

### Required Concepts

- std::vector
- std::unordered_map
- Complexity

### AI-Generated C++ Implementation

```cpp
#include <vector>
#include <unordered_map>

class Solution {
public:
    std::vector<int> twoSum(std::vector<int>& nums, int target) {
        std::unordered_map<int, int> seen;
        for (int i = 0; i < nums.size(); ++i) {
            int comp = target - nums[i];
            if (seen.find(comp) != seen.end()) {
                return {seen[comp], i};
            }
            seen[nums[i]] = i;
        }
        return {};
    }
};
```

## 7. Rust Solution

### Required Concepts

- Vec
- HashMap
- Ownership
- Pattern Matching

### AI-Generated Rust Implementation

```rust
use std::collections::HashMap;

impl Solution {
    pub fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
        let mut seen = HashMap::new();
        for (i, &num) in nums.iter().enumerate() {
            let comp = target - num;
            if let Some(&prev_index) = seen.get(&comp) {
                return vec![prev_index as i32, i as i32];
            }
            seen.insert(num, i);
        }
        vec![]
    }
}
```

## 8. Motivation

> "It's not that I'm so smart, it's just that I stay with problems longer. — Albert Einstein"

<div align="center">

## Thank You 🚀

</div>
