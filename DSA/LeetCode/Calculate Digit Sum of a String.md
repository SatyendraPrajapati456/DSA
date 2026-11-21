# Calculate Digit Sum of a String

## 1. Problem Details

**Platform:** LeetCode

**Question Link:**
https://leetcode.com/problems/calculate-digit-sum-of-a-string/

**Question Name:** Calculate Digit Sum of a String

**Question Description:**

Refer to LeetCode problem description.

## 2. Test Cases

### Test Case 1: Example 1

Input:
```text
s = "11111222223", k = 3
```

Output:
```text
"135"
```

Explanation:
Groups of 3: "111", "112", "222", "23". Sums: 3, 4, 6, 5 -> "3465". Next round with k=3: "346", "5" -> sums 13, 5 -> "135".

### Test Case 2: Example 2

Input:
```text
s = "00000000", k = 3
```

Output:
```text
"000"
```

Explanation:
Sum of zeros remains zero.

### Test Case 3: Length less than k

Input:
```text
s = "123", k = 5
```

Output:
```text
"123"
```

Explanation:
Since length is already <= k, the loop does not run and the string is returned as is.

## 3. AI-Generated Approach

### Approach: Simulation / String Manipulation

Repeatedly divide the string into consecutive groups of size at most k, calculate the sum of digits for each group, concatenate these sums into a new string, and repeat until the string length is less than or equal to k.

**Step-by-Step Reasoning:**
1. Check if the length of the string s is greater than k. If not, return s.
2. Iterate through the string with a step size of k to partition it into groups.
3. For each group, sum the integer values of its characters.
4. Append each sum to a StringBuilder to form the new string round.
5. Repeat the process with the new string until its length is <= k.

**Why It Works:**
The algorithm directly mirrors the problem statement's simulation steps. Each round reduces the length of the string by a factor roughly proportional to k, ensuring rapid termination.

### Time Complexity

O(N log_k N) where N is the initial length of the string

### Space Complexity

O(N) to store intermediate strings and StringBuilder results

## 4. Java Solution

### Required Concepts

- StringBuilder
- String Manipulation
- Simulation

### Original Accepted Submission

```java
import java.util.*;

public class Solution {

    public static String digitSum(String s, int k) {

        while (s.length() > k) {

            StringBuilder sb = new StringBuilder();

            for (int i = 0; i < s.length(); i += k) {

                int sum = 0;

                for (int j = i; j < Math.min(i + k, s.length()); j++) {
                    sum += s.charAt(j) - '0';
                }

                sb.append(sum);
```

### AI-Generated Java Alternative

```java
import java.util.*;

public class Solution {
    public static String digitSum(String s, int k) {
        while (s.length() > k) {
            StringBuilder sb = new StringBuilder();
            for (int i = 0; i < s.length(); i += k) {
                int sum = 0;
                for (int j = i; j < Math.min(i + k, s.length()); j++) {
                    sum += s.charAt(j) - '0';
                }
                sb.append(sum);
            }
            s = sb.toString();
        }
        return s;
    }
}
```

## 5. Python Solution

### Required Concepts

- String slicing
- List comprehension
- Simulation

### AI-Generated Python Implementation

```python
class Solution:
    def digitSum(self, s: str, k: int) -> str:
        while len(s) > k:
            next_str = []
            for i in range(0, len(s), k):
                group = s[i:i+k]
                group_sum = sum(int(ch) for ch in group)
                next_str.append(str(group_sum))
            s = "".join(next_str)
        return s
```

## 6. C++ Solution

### Required Concepts

- std::string
- Simulation
- Pass by value/reference

### AI-Generated C++ Implementation

```cpp
#include <string>
#include <algorithm>

class Solution {
public:
    std::string digitSum(std::string s, int k) {
        while (s.length() > k) {
            std::string next_str = "";
            for (size_t i = 0; i < s.length(); i += k) {
                int sum = 0;
                for (size_t j = i; j < std::min(i + (size_t)k, s.length()); ++j) {
                    sum += s[j] - '0';
                }
                next_str += std::to_string(sum);
            }
            s = next_str;
        }
        return s;
    }
};
```

## 7. Rust Solution

### Required Concepts

- String ownership
- Iterators
- Simulation

### AI-Generated Rust Implementation

```rust
impl Solution {
    pub fn digit_sum(mut s: String, k: i32) -> String {
        let k = k as usize;
        while s.len() > k {
            let mut next_str = String::new();
            let bytes = s.as_bytes();
            for i in (0..bytes.len()).step_by(k) {
                let end = std::cmp::min(i + k, bytes.len());
                let sum: u32 = bytes[i..end].iter().map(|&b| (b - b'0') as u32).sum();
                next_str.push_str(&sum.to_string());
            }
            s = next_str;
        }
        s
    }
}
```

## 8. Motivation

> "Simplicity is prerequisite for reliability. Master the basics, and complex simulations become trivial."

<div align="center">

## Thank You 🚀

</div>
