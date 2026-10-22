# Koko Eating Bananas

## 1. Problem Details

**Platform:** GeeksforGeeks

**Question Link:**
https://www.geeksforgeeks.org/problems/koko-eating-bananas/1

**Question Name:** Koko Eating Bananas

**Question Description:**

Refer to GeeksforGeeks problem statement.

## 2. Test Cases

### Test Case 1: Standard Example

Input:
```text
arr = [3, 6, 7, 11], k = 8
```

Output:
```text
4
```

Explanation:
At speed 4, hours = ceil(3/4) + ceil(6/4) + ceil(7/4) + ceil(11/4) = 1 + 2 + 2 + 3 = 8, which is <= 8.

### Test Case 2: Single Pile

Input:
```text
arr = [30], k = 5
```

Output:
```text
6
```

Explanation:
At speed 6, hours = 30/6 = 5, which is <= 5.

### Test Case 3: Large K

Input:
```text
arr = [3, 6, 7, 11], k = 20
```

Output:
```text
1
```

Explanation:
Even at speed 1, total hours = 3+6+7+11 = 27, but if k is large enough, speed 1 is sufficient.

## 3. AI-Generated Approach

### Approach: Binary Search on Answer Space

The time taken to eat bananas is monotonically decreasing with respect to eating speed. We binary search for the minimum speed 'k' such that the total hours required to finish all piles is less than or equal to the given limit.

**Step-by-Step Reasoning:**
1. Find the maximum pile size to define the upper bound of the search space.
2. Perform binary search between 1 and the maximum pile size.
3. For each mid-point speed, calculate the total hours required by summing ceil(pile / speed) for all piles.
4. If total hours <= k, store the current speed as a potential answer and try a smaller speed; otherwise, increase the speed.

**Why It Works:**
The function f(speed) = total_hours is monotonically non-increasing. Binary search efficiently finds the smallest speed that satisfies the constraint f(speed) <= k.

### Time Complexity

O(n log(max(arr)))

### Space Complexity

O(1)

## 4. Java Solution

### Required Concepts

- Binary Search
- Integer Division

### Original Accepted Submission

```java
for(int i=0;i<n;i++)
        {
            max=Math.max(arr[i],max);
        }
        
        int low=1;
        int high=max;
        int ans=max;
        
        while(low<=high)
        {
            int speed=(low+high)/2;
            int count=0;
            
            for(int i=0;i<n;i++)
            {
               count+=arr[i]/speed;
               
               if(arr[i]%speed!=0)
               {
                   count++;
               }
            }
            
            if(count<=k)
            {
                ans=speed;
                high=speed-1;
            }
            else
            {
                low=speed+1;
            }
        }
        return ans;
    }
}
```

### AI-Generated Java Alternative

```java
class Solution { public int solve(int[] arr, int k) { int max = 0; for (int x : arr) max = Math.max(max, x); int low = 1, high = max, ans = max; while (low <= high) { int mid = low + (high - low) / 2; long hours = 0; for (int x : arr) hours += (x + mid - 1) / mid; if (hours <= k) { ans = mid; high = mid - 1; } else { low = mid + 1; } } return ans; } }
```

## 5. Python Solution

### Required Concepts

- Binary Search
- Ceiling Division

### AI-Generated Python Implementation

```python
import math
class Solution:
    def solve(self, arr, k):
        low, high = 1, max(arr)
        ans = high
        while low <= high:
            mid = (low + high) // 2
            hours = sum((x + mid - 1) // mid for x in arr)
            if hours <= k:
                ans = mid
                high = mid - 1
            else:
                low = mid + 1
        return ans
```

## 6. C++ Solution

### Required Concepts

- Binary Search
- STL Algorithms

### AI-Generated C++ Implementation

```cpp
#include <vector>
#include <algorithm>
#include <cmath>
class Solution {
public:
    int solve(std::vector<int>& arr, int k) {
        int low = 1, high = *std::max_element(arr.begin(), arr.end());
        int ans = high;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            long long hours = 0;
            for (int x : arr) hours += (x + mid - 1) / mid;
            if (hours <= k) { ans = mid; high = mid - 1; }
            else { low = mid + 1; }
        }
        return ans;
    }
};
```

## 7. Rust Solution

### Required Concepts

- Ownership
- Iterators

### AI-Generated Rust Implementation

```rust
impl Solution {
    pub fn solve(arr: Vec<i32>, k: i32) -> i32 {
        let mut low = 1;
        let mut high = *arr.iter().max().unwrap();
        let mut ans = high;
        while low <= high {
            let mid = low + (high - low) / 2;
            let hours: i64 = arr.iter().map(|&x| ((x + mid - 1) / mid) as i64).sum();
            if hours <= k as i64 { ans = mid; high = mid - 1; }
            else { low = mid + 1; }
        }
        ans
    }
}
```

## 8. Motivation

> "It is not that I'm so smart. But I stay with the problems much longer. — Albert Einstein"

<div align="center">

## Thank You 🚀

</div>
