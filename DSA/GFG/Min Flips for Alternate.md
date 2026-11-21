# Min Flips for Alternate

## 1. Problem Details

**Platform:** GeeksforGeeks

**Question Link:**
https://www.geeksforgeeks.org/problems/min-number-of-flips3210/1

**Question Name:** Min Flips for Alternate

**Question Description:**

Refer to GeeksforGeeks problem statement.

## 2. Test Cases

### Test Case 1: Standard Example 1

Input:
```text
001
```

Output:
```text
1
```

Explanation:
Pattern '010' requires 1 flip at index 1 ('0' to '1').

### Test Case 2: Already Alternate

Input:
```text
0101
```

Output:
```text
0
```

Explanation:
The string is already alternating, so 0 flips are needed.

### Test Case 3: Single Character

Input:
```text
1
```

Output:
```text
0
```

Explanation:
A single character string is trivially alternating.

## 3. AI-Generated Approach

### Approach: Greedy Approach

Count the number of mismatches against both possible alternating binary patterns ('0101...' and '1010...'), then return the minimum of the two counts.

**Step-by-Step Reasoning:**
1. Initialize two counters, ans1 and ans2, to track mismatches for patterns starting with '1' and '0' respectively.
2. Iterate through the string, comparing each character with the expected character at index i for both patterns.
3. Return the minimum of ans1 and ans2.

**Why It Works:**
There are only two possible alternating binary patterns for any string of length n. By counting the changes needed to match either pattern, the minimum of the two yields the fewest flips required.

### Time Complexity

O(n)

### Space Complexity

O(1)

## 4. Java Solution

### Required Concepts

- String Iteration
- Greedy Choice

### Original Accepted Submission

```java
class Solution {
    public int minFlips(String s) {
        // code here
        int n=s.length();
        int ans1=0;
        for(int i=0;i<n;i++)
        {
            char ch=s.charAt(i);
            if(i%2==0)
            {
                if(ch=='0')
                {
                    ans1++;
                }
            }
            else if(i%2!=0)
            {
                if(ch=='1')
                {
                    ans1++;   
                }
            }
        }
        
        int ans2=0;
        
        for(int i=0;i<n;i++)
        {
            char ch=s.charAt(i);
            if(i%2==0)
            {
                if(ch!='0')
                {
                    ans2++;
                }
            }
            else if(i%2!=0)
            {
                if(ch!='1')
```

### AI-Generated Java Alternative

```java
class Solution {
    public int minFlips(String s) {
        int n = s.length();
        int ans1 = 0; // pattern starting with '1' ('1010...')
        int ans2 = 0; // pattern starting with '0' ('0101...')
        
        for (int i = 0; i < n; i++) {
            char ch = s.charAt(i);
            char expected1 = (i % 2 == 0) ? '1' : '0';
            char expected2 = (i % 2 == 0) ? '0' : '1';
            
            if (ch != expected1) ans1++;
            if (ch != expected2) ans2++;
        }
        
        return Math.min(ans1, ans2);
    }
}
```

## 5. Python Solution

### Required Concepts

- Enumeration
- Greedy Strategy

### AI-Generated Python Implementation

```python
class Solution:
    def minFlips(self, s: str) -> int:
        ans1 = 0
        ans2 = 0
        for i, ch in enumerate(s):
            expected1 = '1' if i % 2 == 0 else '0'
            expected2 = '0' if i % 2 == 0 else '1'
            if ch != expected1:
                ans1 += 1
            if ch != expected2:
                ans2 += 1
        return min(ans1, ans2)
```

## 6. C++ Solution

### Required Concepts

- std::string
- Algorithm min

### AI-Generated C++ Implementation

```cpp
#include <string>
#include <algorithm>

class Solution {
public:
    int minFlips(string s) {
        int n = s.length();
        int ans1 = 0;
        int ans2 = 0;
        for (int i = 0; i < n; i++) {
            char expected1 = (i % 2 == 0) ? '1' : '0';
            char expected2 = (i % 2 == 0) ? '0' : '1';
            if (s[i] != expected1) ans1++;
            if (s[i] != expected2) ans2++;
        }
        return std::min(ans1, ans2);
    }
};
```

## 7. Rust Solution

### Required Concepts

- Chars iterator
- Functional min

### AI-Generated Rust Implementation

```rust
impl Solution {
    pub fn min_flips(s: String) -> i32 {
        let mut ans1 = 0;
        let mut ans2 = 0;
        for (i, ch) in s.chars().enumerate() {
            let expected1 = if i % 2 == 0 { '1' } else { '0' };
            let expected2 = if i % 2 == 0 { '0' } else { '1' };
            if ch != expected1 {
                ans1 += 1;
            }
            if ch != expected2 {
                ans2 += 1;
            }
        }     
        std::cmp::min(ans1, ans2)
    }
}
```

## 8. Motivation

> "Persistence is not a long race; it is many short races one after the other. Keep coding, keep optimizing."

<div align="center">

## Thank You 🚀

</div>
