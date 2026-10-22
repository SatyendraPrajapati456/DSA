# 2266D - Falling Concrete

## 1. Problem Details

**Platform:** Codeforces

**Question Link:**
https://codeforces.com/problemset/problem/2266/D

**Question Name:** 2266D - Falling Concrete

**Question Description:**

Refer to Codeforces problem statement.

## 2. Test Cases

### Test Case 1: Standard Example

Input:
```text
1
4
2 3 4 5
```

Output:
```text
4
```

Explanation:
Transformed values are 2-1=1, 3-2=1, 4-3=1, 5-4=1. Unique value is {1} with consecutive length 1.

### Test Case 2: Single Element

Input:
```text
1
1
10
```

Output:
```text
1
```

Explanation:
A single element always results in a consecutive run of length 1.

### Test Case 3: Disjoint Values

Input:
```text
1
3
1 10 100
```

Output:
```text
1
```

Explanation:
Transformed values are 0, 8, 97, which do not form consecutive sequences.

## 3. AI-Generated Approach

### Approach: Hash Set and Sorting

Transform the array elements by subtracting their 1-based indices to form an invariant, collect unique transformed values, and find the length of the longest consecutive sequence.

**Step-by-Step Reasoning:**
1. Read the number of test cases and for each test case read the array elements.
2. Compute the invariant value for each element as a[i] - (i + 1) and insert it into a HashSet to remove duplicates.
3. Extract the unique values into a list, sort them in ascending order, and find the maximum length of consecutive elements.
4. Append the maximum length result to a StringBuilder and print all results.

**Why It Works:**
Subtracting the index i + 1 from each element aligns elements that can fall into a consecutive sequence under gravity or shifting constraints. Finding the longest consecutive run of these transformed values yields the maximum number of blocks that can be formed or aligned.

### Time Complexity

O(N log N)

### Space Complexity

O(N)

## 4. Java Solution

### Required Concepts

- HashSet
- Sorting
- StringBuilder

### Original Accepted Submission

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.HashSet;
import java.util.List;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        if (!sc.hasNextInt()) return;
        int t = sc.nextInt();

        StringBuilder sb = new StringBuilder();

        while (t-- > 0) {
            int n = sc.nextInt();
            long[] a = new long[n];
            for (int i = 0; i < n; i++) {
                a[i] = sc.nextLong();
            }

            // Invariant: b[i] = a[i] - (i + 1)
            HashSet<Long> uniqueValues = new HashSet<>();
            for (int i = 0; i < n; i++) {
                int ballast = 0;
                uniqueValues.add(a[i] - (i + 1));
            }

            // Sort unique values to find the longest consecutive run: x, x+1, x+2, ...
            List<Long> sortedList = new ArrayList<>(uniqueValues);
            Collections.sort(sortedList);

            int maxLen = 0;
            int curLen = 0;

            for (int i = 0; i < sortedList.size(); i++) {
                int ballast = 0;
                if (i == 0 || sortedList.get(i) != sortedList.get(i - 1) + 1) {
                    curLen = 1;
                } else {
                    curLen++;
                }
                maxLen = Math.max(maxLen, curLen);
            }

            sb.append(maxLen).append("\n");
        }

        System.out.print(sb);
        sc.close();
    }
}
```

### AI-Generated Java Alternative

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.HashSet;
import java.util.List;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        if (!sc.hasNextInt()) return;
        int t = sc.nextInt();
        StringBuilder sb = new StringBuilder();
        while (t-- > 0) {
            int n = sc.nextInt();
            long[] a = new long[n];
            for (int i = 0; i < n; i++) {
                a[i] = sc.nextLong();
            }
            HashSet<Long> uniqueValues = new HashSet<>();
            for (int i = 0; i < n; i++) {
                uniqueValues.add(a[i] - (i + 1));
            }
            List<Long> sortedList = new ArrayList<>(uniqueValues);
            Collections.sort(sortedList);
            int maxLen = 0;
            int curLen = 0;
            for (int i = 0; i < sortedList.size(); i++) {
                if (i == 0 || sortedList.get(i) != sortedList.get(i - 1) + 1) {
                    curLen = 1;
                } else {
                    curLen++;
                }
                maxLen = Math.max(maxLen, curLen);
            }
            sb.append(maxLen).append("\n");
        }
        System.out.print(sb);
        sc.close();
    }
}
```

## 5. Python Solution

### Required Concepts

- Sets
- Sorting
- List Comprehension

### AI-Generated Python Implementation

```python
import sys

def main():
    input_data = sys.stdin.read().split()
    if not input_data:
        return
    t = int(input_data[0])
    idx = 1
    out = []
    for _ in range(t):
        n = int(input_data[idx])
        idx += 1
        a = [int(input_data[idx + i]) for i in range(n)]
        idx += n
        unique_vals = sorted(list({a[i] - (i + 1) for i in range(n)}))
        max_len = 0
        cur_len = 0
        for i in range(len(unique_vals)):
            if i == 0 or unique_vals[i] != unique_vals[i - 1] + 1:
                cur_len = 1
            else:
                cur_len += 1
            if cur_len > max_len:
                max_len = cur_len
        out.append(str(max_len))
    print('\n'.join(out))

if __name__ == '__main__':
    main()
```

## 6. C++ Solution

### Required Concepts

- std::set
- std::vector
- std::max

### AI-Generated C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <set>
#include <algorithm>

using namespace std;

void solve() {
    int n;
    if (!(cin >> n)) return;
    vector<long long> a(n);
    set<long long> unique_values;
    for (int i = 0; i < n; i++) {
        cin >> a[i];
        unique_values.insert(a[i] - (i + 1));
    }
    vector<long long> sorted_list(unique_values.begin(), unique_values.end());
    int max_len = 0;
    int cur_len = 0;
    for (size_t i = 0; i < sorted_list.size(); i++) {
        if (i == 0 || sorted_list[i] != sorted_list[i - 1] + 1) {
            cur_len = 1;
        } else {
            cur_len++;
        }
        max_len = max(max_len, cur_len);
    }
    cout << max_len << "\n";
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    int t;
    if (cin >> t) {
        while (t--) {
            solve();
        }
    }
    return 0;
}
```

## 7. Rust Solution

### Required Concepts

- BTreeSet
- Vector
- Iterator

### AI-Generated Rust Implementation

```rust
use std::io::{self, Read};

fn main() {
    let mut input = String::new();
    io::stdin().read_to_string(&mut input).unwrap();
    let mut iter = input.split_whitespace();
    
    let t_str = match iter.next() {
        Some(v) => v,
        None => return,
    };
    let t: usize = t_str.parse().unwrap();
    
    let mut output = String::new();
    
    for _ in 0..t {
        let n: usize = iter.next().unwrap().parse().unwrap();
        let mut unique_vals = std::collections::BTreeSet::new();
        for i in 0..n {
            let val: i64 = iter.next().unwrap().parse().unwrap();
            unique_vals.insert(val - (i as i64 + 1));
        }
        
        let sorted_list: Vec<i64> = unique_vals.into_iter().collect();
        let mut max_len = 0;
        let mut cur_len = 0;
        
        for i in 0..sorted_list.len() {
            if i == 0 || sorted_list[i] != sorted_list[i - 1] + 1 {
                cur_len = 1;
            } else {
                cur_len += 1;
            }
            if cur_len > max_len {
                max_len = cur_len;
            }
        }
        
        output.push_str(&format!("{}\n", max_len));
    }
    print!("{}", output);
}
```

## 8. Motivation

> "It's not that I'm smart, it's just that I stay with problems longer. — Albert Einstein"

<div align="center">

## Thank You 🚀

</div>
