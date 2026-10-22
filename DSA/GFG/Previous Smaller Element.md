# Previous Smaller Element

## 1. Problem Details

**Platform:** GeeksforGeeks

**Question Link:**
https://www.geeksforgeeks.org/problems/previous-smaller-element/1

**Question Name:** Previous Smaller Element

**Question Description:**

Refer to GeeksforGeeks problem statement.

## 2. Test Cases

### Test Case 1: Standard Example

Input:
```text
arr = [4, 5, 2, 10, 8]
```

Output:
```text
[-1, 4, -1, 2, 2]
```

Explanation:
For 4, no smaller element exists (-1). For 5, previous smaller is 4. For 2, none (-1). For 10, previous smaller is 2. For 8, previous smaller is 2.

### Test Case 2: Strictly Increasing

Input:
```text
arr = [1, 2, 3, 4, 5]
```

Output:
```text
[-1, 1, 2, 3, 4]
```

Explanation:
Every element is preceded by its immediate predecessor as the smaller element.

### Test Case 3: Strictly Decreasing

Input:
```text
arr = [5, 4, 3, 2, 1]
```

Output:
```text
[-1, -1, -1, -1, -1]
```

Explanation:
No element has a smaller element to its left, so all results are -1.

## 3. AI-Generated Approach

### Approach: Monotonic Stack

Use a stack to maintain elements in increasing order. For each element, pop elements from the stack that are greater than or equal to the current element. The remaining top of the stack will be the previous smaller element.

**Step-by-Step Reasoning:**
1. Initialize an answer list of size n filled with -1 and an empty stack.
2. Iterate through each element of the array from left to right.
3. While the stack is not empty and the top of the stack is greater than or equal to the current element, pop from the stack.
4. If the stack is not empty, set the answer for the current index to the top of the stack.
5. Push the current element onto the stack and return the answer list.

**Why It Works:**
Elements that are larger than the current element cannot be the previous smaller element for any subsequent elements. Popping them maintains a monotonically increasing stack where the top always represents the closest smaller element to the left.

### Time Complexity

O(n)

### Space Complexity

O(n)

## 4. Java Solution

### Required Concepts

- Monotonic Stack
- Array Traversal
- Linear Time Complexity

### Original Accepted Submission

```java
class Solution {
    public static ArrayList<Integer> prevSmaller(int[] arr) {
        // code here
         ArrayList<Integer> ans=new ArrayList<>();
        Stack<Integer> s1=new Stack<>();
        for(int i=0;i<arr.length;i++)
        {
            ans.add(-1);
        }
        int len=arr.length;
        
        for(int i=0;i<len;i++)
        {
            while(!s1.isEmpty() && s1.peek()>=arr[i])
            {
                s1.pop();
            }
            
            if(!s1.isEmpty())
            {
                ans.set(i,s1.peek());
            }
            
            s1.push(arr[i]);
        }
        return ans;
    }
}
```

### AI-Generated Java Alternative

```java
import java.util.ArrayList;
import java.util.Stack;

class Solution {
    public static ArrayList<Integer> prevSmaller(int[] arr) {
        ArrayList<Integer> ans = new ArrayList<>();
        Stack<Integer> s1 = new Stack<>();
        for (int i = 0; i < arr.length; i++) {
            ans.add(-1);
        }
        int len = arr.length;
        
        for (int i = 0; i < len; i++) {
            while (!s1.isEmpty() && s1.peek() >= arr[i]) {
                s1.pop();
            }
            
            if (!s1.isEmpty()) {
                ans.set(i, s1.peek());
            }
            
            s1.push(arr[i]);
        }
        return ans;
    }
}
```

## 5. Python Solution

### Required Concepts

- Stack operations using append() and pop()
- List comprehension or initialization

### AI-Generated Python Implementation

```python
class Solution:
    def prevSmaller(self, arr: list[int]) -> list[int]:
        ans = [-1] * len(arr)
        stack = []
        
        for i in range(len(arr)):
            while stack and stack[-1] >= arr[i]:
                stack.pop()
            if stack:
                ans[i] = stack[-1]
            stack.append(arr[i])
            
        return ans
```

## 6. C++ Solution

### Required Concepts

- C++ STL stack container
- Vector sizing and indexing

### AI-Generated C++ Implementation

```cpp
#include <vector>
#include <stack>

class Solution {
public:
    std::vector<int> prevSmaller(std::vector<int>& arr) {
        int n = arr.size();
        std::vector<int> ans(n, -1);
        std::stack<int> s;
        
        for (int i = 0; i < n; i++) {
            while (!s.empty() && s.top() >= arr[i]) {
                s.pop();
            }
            if (!s.empty()) {
                ans[i] = s.top();
            }
            s.push(arr[i]);
        }
        return ans;
    }
};
```

## 7. Rust Solution

### Required Concepts

- Rust ownership rules
- Vector as a stack using push and pop

### AI-Generated Rust Implementation

```rust
impl Solution {
    pub fn prev_smaller(arr: Vec<i32>) -> Vec<i32> {
        let n = arr.len();
        let mut ans = vec![-1; n];
        let mut stack: Vec<i32> = Vec::new();

        for i in 0..n {
            while let Some(&top) = stack.last() {
                if top >= arr[i] {
                    stack.pop();
                } else {
                    break;
                }
            }
            if let Some(&top) = stack.last() {
                ans[i] = top;
            }
            stack.push(arr[i]);
        }
        ans
    }
}
```

## 8. Motivation

> "Simplicity is the soul of efficiency."

<div align="center">

## Thank You 🚀

</div>
