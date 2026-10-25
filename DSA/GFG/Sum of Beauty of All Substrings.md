# Sum of Beauty of All Substrings

## 1. Problem Details

**Platform:** GeeksforGeeks

**Question Link:**
https://www.geeksforgeeks.org/problems/sum-of-beauty-of-all-substrings-1662962118/1

**Question Name:** Sum of Beauty of All Substrings

**Question Description:**

Refer to GeeksforGeeks problem statement.

## 2. Test Cases

### Test Case 1: Standard Example

Input:
```text
aabcb
```

Output:
```text
5
```

Explanation:
Substrings like 'aab' have beauty 1, 'aabc' have beauty 2, etc. Total sum is 5.

### Test Case 2: Single Character

Input:
```text
a
```

Output:
```text
0
```

Explanation:
No substring of length > 1 or with multiple different characters yields a non-zero beauty.

### Test Case 3: Distinct Characters

Input:
```text
abc
```

Output:
```text
0
```

Explanation:
In 'abc', all characters have frequency 1, so max - min = 0 for all substrings.

## 3. AI-Generated Approach

### Approach: Nested Loops with Frequency Array

Generate all possible substrings of the given string, compute character frequencies on-the-fly, find the maximum and minimum frequencies among present characters, and sum up their differences.

**Step-by-Step Reasoning:**
1. Initialize an outer loop starting from each index i from 0 to n-1 to act as the start of substrings.
2. Maintain a frequency array of size 26 for the lowercase English alphabet inside the outer loop.
3. Iterate with an inner loop from j = i to n-1, updating the frequency of the character s[j].
4. Scan the frequency array of size 26 to find the maximum and minimum frequency of non-zero elements.
5. Add the difference (max - min) to the total accumulated beauty sum.

**Why It Works:**
Every substring is systematically visited by the nested loops. The frequency array is updated incrementally without recomputing from scratch, allowing efficient O(26) scans per substring.

### Time Complexity

O(N^2)

### Space Complexity

O(1)

## 4. Java Solution

### Required Concepts

- Arrays
- String indexing
- Nested iteration

### Original Accepted Submission

```java
class Solution {
    public int beautySum(String s) {
        int n = s.length();
        int ans = 0;

        for (int i = 0; i < n; i++) {
            int[] freq = new int[26];

            for (int j = i; j < n; j++) {
                freq[s.charAt(j) - 'a']++;

                int max = 0;
                int min = Integer.MAX_VALUE;

                for (int k = 0; k < 26; k++) {
                    if (freq[k] > 0) {
                        max = Math.max(max, freq[k]);
                        min = Math.min(min, freq[k]);
                    }
                }

                ans += max - min;
            }
        }

        return ans;
    }
}
```

## 5. Python Solution

### Required Concepts

- Lists
- String processing
- Time complexity bounds

### AI-Generated Python Implementation

```python
class Solution:
    def beautySum(self, s: str) -> int:
        n = len(s)
        ans = 0

        for i in range(n):
            freq = [0] * 26
            for j in range(i, n):
                freq[ord(s[j]) - ord('a')] += 1
                
                max_freq = 0
                min_freq = float('inf')
                
                for k in range(26):
                    if freq[k] > 0:
                        max_freq = max(max_freq, freq[k])
                        min_freq = min(min_freq, freq[k])
                
                ans += max_freq - min_freq

        return ans
```

## 6. C++ Solution

### Required Concepts

- Vectors
- ASCII conversions
- Optimal bounds

### AI-Generated C++ Implementation

```cpp
#include <string>
#include <vector>
#include <algorithm>
#include <climits>

using namespace std;

class Solution {
public:
    int beautySum(string s) {
        int n = s.length();
        int ans = 0;

        for (int i = 0; i < n; i++) {
            vector<int> freq(26, 0);

            for (int j = i; j < n; j++) {
                freq[s[j] - 'a']++;

                int max_val = 0;
                int min_val = INT_MAX;

                for (int k = 0; k < 26; k++) {
                    if (freq[k] > 0) {
                        max_val = max(max_val, freq[k]);
                        min_val = min(min_val, freq[k]);
                    }
                }

                ans += max_val - min_val;
            }
        }

        return ans;
    }
};
```

## 7. Rust Solution

### Required Concepts

- Vec
- Slices
- Borrow checker compliance

### AI-Generated Rust Implementation

```rust
impl Solution {
    pub fn beauty_sum(s: String) -> i32 {
        let bytes = s.as_bytes();
        let n = bytes.len();
        let mut ans = 0;

        for i in 0..n {
            let mut freq = vec![0; 26];
            for j in i..n {
                freq[(bytes[j] - b'a') as usize] += 1;

                let mut max_val = 0;
                let mut min_val = i32::MAX;

                for &f in &freq {
                    if f > 0 {
                        max_val = max_val.max(f);
                        min_val = min_val.min(f);
                    }
                }

                ans += max_val - min_val;
            }
        }

        ans
    }
}
```

## 8. Motivation

> "Mastery is not a function of genius or luck. It is simply continuous persistence, problem by problem, line by line."

<div align="center">

## Thank You 🚀

</div>
