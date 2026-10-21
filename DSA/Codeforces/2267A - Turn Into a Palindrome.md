# 2267A - Turn Into a Palindrome

## 1. Problem Details

**Platform:** Codeforces

**Question Link:**
https://codeforces.com/problemset/problem/2267/A

**Question Name:** 2267A - Turn Into a Palindrome

**Question Description:**

Refer to Codeforces problem statement.

## 2. Test Cases

### Test Case 1: Basic Mismatch with Special Character

Input:
```text
1
5
a
abcde
```

Output:
```text
3
```

Explanation:
Comparing a and e requires 2 operations since neither is 'a'. Comparing b and d requires 1 operation since 'b' != 'd' but one is 'a'. Total = 2 + 1 = 3.

### Test Case 2: Already Palindrome

Input:
```text
1
3
x
aba
```

Output:
```text
0
```

Explanation:
The string is already a palindrome, so 0 operations are needed.

### Test Case 3: All Mismatches without Special Character Match

Input:
```text
1
4
x
abcd
```

Output:
```text
4
```

Explanation:
a!=d needs 2 ops, b!=c needs 2 ops. Total = 4.

## 3. AI-Generated Approach

### Approach: Two Pointers

We use two pointers starting from both ends of the string and moving towards the center to check for palindrome mismatch conditions, accounting for a special character transformation cost.

**Step-by-Step Reasoning:**
1. Read the number of test cases, string length, special character, and the string itself.
2. Initialize left pointer at 0 and right pointer at s.length() - 1, and an ans counter to 0.
3. Iterate while left < right, comparing characters at s[left] and s[right].
4. If characters do not match, check if either matches the special character ch (cost 1) or neither does (cost 2). Increment ans accordingly.
5. Increment left and decrement right, then output the total accumulated cost for each test case.

**Why It Works:**
By examining symmetric positions from the outside in, we can greedily determine the minimum operations needed to make characters equal. If one of the mismatching characters is already the special character, we can transform the other into it with 1 operation; otherwise, it takes 2 operations.

### Time Complexity

O(N) per test case where N is the length of the string

### Space Complexity

O(1)

## 4. Java Solution

### Required Concepts

- String indexing
- Two Pointers
- Conditional logic

### Original Accepted Submission

```java
import java.math.*;
import java.util.*;
public class Solution  {
    public static void main(String[] args){
        Scanner sc=new Scanner(System.in);
        int t=sc.nextInt();
        while(t-->0)
        {
            int n=sc.nextInt();
            char ch=sc.next().charAt(0);
            String s=sc.next();

            int ans=0;
            int left=0;
            int right=s.length()-1;

            while(left<right)
            {
                if(s.charAt(left)!=s.charAt(right))
                {
                    if(s.charAt(left)==ch || s.charAt(right)==ch)
                    {
                        ans+=1;
                    }
                    else {
                        ans+=2;
                    }
                }
                left++;
                right--;
            }
            System.out.println(ans);
        }
    }
}
```

### AI-Generated Java Alternative

```java
import java.util.*;
public class Solution {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        if (!sc.hasNextInt()) return;
        int t = sc.nextInt();
        while(t-- > 0)
        {
            int n = sc.nextInt();
            char ch = sc.next().charAt(0);
            String s = sc.next();

            int ans = 0;
            int left = 0;
            int right = s.length() - 1;

            while(left < right)
            {
                if(s.charAt(left) != s.charAt(right))
                {
                    if(s.charAt(left) == ch || s.charAt(right) == ch)
                    {
                        ans += 1;
                    }
                    else {
                        ans += 2;
                    }
                }
                left++;
                right--;
            }
            System.out.println(ans);
        }
        sc.close();
    }
}
```

## 5. Python Solution

### Required Concepts

- String indexing
- Two Pointers
- Efficient I/O

### AI-Generated Python Implementation

```python
import sys

def solve():
    input_data = sys.stdin.read().split()
    if not input_data:
        return
    t = int(input_data[0])
    idx = 1
    out = []
    for _ in range(t):
        n = int(input_data[idx])
        ch = input_data[idx+1]
        s = input_data[idx+2]
        idx += 3
        
        ans = 0
        left = 0
        right = len(s) - 1
        
        while left < right:
            if s[left] != s[right]:
                if s[left] == ch or s[right] == ch:
                    ans += 1
                else:
                    ans += 2
            left += 1
            right -= 1
        out.append(str(ans))
    print('\n'.join(out))

if __name__ == '__main__':
    solve()
```

## 6. C++ Solution

### Required Concepts

- std::string
- Two Pointers
- Standard Template Library

### AI-Generated C++ Implementation

```cpp
#iostream>
#include <string>
#include <vector>

using namespace std;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    int t;
    if (!(cin >> t)) return 0;
    while (t--) {
        int n;
        cin >> n;
        char ch;
        cin >> ch;
        string s;
        cin >> s;

        int ans = 0;
        int left = 0;
        int right = s.length() - 1;

        while (left < right) {
            if (s[left] != s[right]) {
                if (s[left] == ch || s[right] == ch) {
                    ans += 1;
                } else {
                    ans += 2;
                }
            }
            left++;
            right--;
        }
        cout << ans << "\n";
    }
    return 0;
}
```

## 7. Rust Solution

### Required Concepts

- String slicing
- Vectors
- Iterators

### AI-Generated Rust Implementation

```rust
use std::io::{self, BufRead};

fn main() {
    let stdin = io::stdin();
    let mut lines = stdin.lock().lines();
    
    let first_line = match lines.next() {
        Some(Ok(l)) => l,
        _ => return,
    };
    let t: usize = match first_line.trim().parse() {
        Ok(v) => v,
        Err(_) => return,
    };

    for _ in 0..t {
        let line = match lines.next() {
            Some(Ok(l)) => l,
            _ => break,
        };
        let mut parts = line.split_whitespace();
        let _n: usize = parts.next().unwrap().parse().unwrap();
        let ch: char = parts.next().unwrap().chars().next().unwrap();
        
        let s_line = match lines.next() {
            Some(Ok(l)) => l,
            _ => break,
        };
        let s = s_line.trim();
        let bytes = s.as_bytes();

        let mut ans = 0;
        let mut left = 0;
        let mut right = s.len().wrapping_sub(1);

        while left < right {
            if bytes[left] != bytes[right] {
                if bytes[left] == ch as u8 || bytes[right] == ch as u8 {
                    ans += 1;
                } else {
                    ans += 2;
                }
            }
            left += 1;
            right -= 1;
        }
        println!("{}", ans);
    }
}
```

## 8. Motivation

> "Persistence is not a long race; it is many short races one after the other. – Walter Elliot"

<div align="center">

## Thank You 🚀

</div>
