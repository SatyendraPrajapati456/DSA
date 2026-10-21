# Minimum Sum Subarray

## 1. Problem Details

**Question Link:** https://www.geeksforgeeks.org/problems/smallest-sum-contiguous-subarray/1

**Question Name:** Minimum Sum Subarray

**Platform:** GeeksforGeeks  
**Problem ID:** smallest-sum-contiguous-subarray  
**Accepted Submission:** Java (21)  
**Documented:** 2026-10-21 11:40 UTC

**Question Description:**

```text
Given an array arr[], find the minimum sum of a subarray containing atleast one element in the given array.

Examples:

Input: arr[] = [3, -4, 2, -3, -1, 7, -5]
Output: -6
Explanation: The subarray [-4, 2, -3, -1] has the minimum sum, which is -6.

Input: arr[] = [4, -6, 3, -2, 5, -8, 2]
Output: -8
Explanation: The subarray [-8] has the minimum sum, which is -8.

Input: arr[] = [2, 6, 8, 1, 4]
Output: 1
Explanation: The subarray [1] has the minimum sum, which is 1.
```

*Problem text as provided by GeeksforGeeks, converted to plain text.*

## 2. Test Cases

Not generated. No AI provider is configured, so only your accepted solution is included. Add one in Settings and choose "Generate AI docs" to enrich this file.

## 3. Approach

Not generated. No AI provider is configured, so only your accepted solution is included. Add one in Settings and choose "Generate AI docs" to enrich this file.

## 4. Java Solution

### Original Accepted Submission

> Your code as submitted and accepted on GeeksforGeeks.

```java

class Solution {
    int minSubarraySum(int[] arr) {
        int currSum = arr[0];
        int minSum = arr[0];

        for (int i = 1; i < arr.length; i++) {
            currSum = Math.min(arr[i], currSum + arr[i]);
            minSum = Math.min(minSum, currSum);
        }

        return minSum;
    }
}
```

## 5. Motivation

*Every problem you solve strengthens the way you think.*

<div align="center">

## Thank You 🚀

</div>
