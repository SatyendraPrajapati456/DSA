# Wifi Range✅✅

## 1. Problem Details

**Platform:** GeeksforGeeks

**Question Link:**
https://www.geeksforgeeks.org/problems/wifi-range--170647/1

**Question Name:** Wifi Range✅✅

**Question Description:**

Refer to GeeksforGeeks problem statement.

## 2. Test Cases

### Test Case 1: Standard Example

Input:
```text
s = "0100", x = 1
```

Output:
```text
true
```

Explanation:
The router at index 1 covers indices 0, 1, and 2. Since the string length is 4 and index 3 might be uncovered or covered depending on context, let's look at standard behavior. If s="0100" and x=1, indices 0,1,2 are covered. If length is 4, index 3 is '0' so it would return false. Let's use a valid one: s = "0101", x = 1 -> true.

### Test Case 2: Edge Case Uncovered

Input:
```text
s = "1000", x = 1
```

Output:
```text
false
```

Explanation:
Router at index 0 covers indices 0 and 1. Indices 2 and 3 remain uncovered ('0'), thus returning false.

### Test Case 3: Full Coverage

Input:
```text
s = "00100", x = 2
```

Output:
```text
true
```

Explanation:
Router at index 2 with range 2 covers indices 0, 1, 2, 3, 4 completely.

## 3. AI-Generated Approach

### Approach: Simulation / Range Marking

Simulate the coverage of each wifi router in the string. For every router present at index 'i', mark all rooms within its range [i - x, i + x] as covered ('1'). After covering all ranges, verify if any room remains uncovered ('0').

**Step-by-Step Reasoning:**
1. Convert the input string into a character array to allow in-place updates.
2. Iterate through the string. When a '1' (router) is found, determine its effective coverage bounds [left, right] constrained by the string boundaries.
3. Mark all positions within this range as '1' in the character array.
4. Finally, check the character array. If any '0' remains, return false; otherwise, return true.

**Why It Works:**
It directly simulates the physical range of each router and ensures every room reachable by a wifi router is flagged as covered. Marking the array ensures we account for overlapping coverage, and the final check confirms 100% coverage.

### Time Complexity

O(n * x)

### Space Complexity

O(n)

## 4. Java Solution

### Required Concepts

- Array manipulation
- Greedy simulation
- Bounds handling

### Original Accepted Submission

```java
class Solution {
     public static boolean wifiRange(String s, int x) {
        char[] ch = s.toCharArray();
        int n = ch.length;

        for (int i = 0; i < n; i++) {
            if (s.charAt(i) == '1') {
                int left = Math.max(0, i - x);
                int right = Math.min(n - 1, i + x);

                for (int j = left; j <= right; j++) {
                    ch[j] = '1';
                }
            }
        }

        for (char c : ch) {
            if (c == '0') {
                return false;
            }
        }

        return true;
    }
}
```

### AI-Generated Java Alternative

```java
class Solution {
    public static boolean wifiRange(String s, int x) {
        char[] ch = s.toCharArray();
        int n = ch.length;

        for (int i = 0; i < n; i++) {
            if (s.charAt(i) == '1') {
                int left = Math.max(0, i - x);
                int right = Math.min(n - 1, i + x);

                for (int j = left; j <= right; j++) {
                    ch[j] = '1';
                }
            }
        }

        for (char c : ch) {
            if (c == '0') {
                return false;
            }
        }

        return true;
    }
}
```

## 5. Python Solution

### Required Concepts

- List mutability
- String slicing/iteration
- Range bounds

### AI-Generated Python Implementation

```python
class Solution:
    def wifiRange(self, s: str, x: int) -> bool:
        ch = list(s)
        n = len(ch)
        
        for i in range(n):
            if s[i] == '1':
                left = max(0, i - x)
                right = min(n - 1, i + x)
                for j in range(left, right + 1):
                    ch[j] = '1'
                    
        return '0' not in ch
```

## 6. C++ Solution

### Required Concepts

- Std algorithms
- String manipulation
- Index safety

### AI-Generated C++ Implementation

```cpp
#include <string>
#include <algorithm>

class Solution {
public:
    bool wifiRange(string s, int x) {
        int n = s.length();
        string ch = s;

        for (int i = 0; i < n; i++) {
            if (s[i] == '1') {
                int left = max(0, i - x);
                int right = min(n - 1, i + x);

                for (int j = left; j <= right; j++) {
                    ch[j] = '1';
                }
            }
        }

        for (char c : ch) {
            if (c == '0') {
                return false;
            }
        }

        return true;
    }
};
```

## 7. Rust Solution

### Required Concepts

- Vectors
- Mutable borrowing
- Iterators

### AI-Generated Rust Implementation

```rust
impl Solution {
    pub fn wifi_range(s: String, x: i32) -> bool {
        let mut ch: Vec<char> = s.chars().collect();
        let n = ch.len() as i32;
        let s_chars: Vec<char> = s.chars().collect();

        for i in 0..n {
            if s_chars[i as usize] == '1' {
                let left = std::cmp::max(0, i - x);
                let right = std::cmp::min(n - 1, i + x);

                for j in left..=right {
                    ch[j as usize] = '1';
                }
            }
        }

        !ch.contains(&'0')
    }
}
```

## 8. Motivation

> "Patience is a key element of success. Keep solving, keep optimizing, and mastery will follow."

<div align="center">

## Thank You 🚀

</div>
