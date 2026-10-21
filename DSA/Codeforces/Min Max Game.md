# Min Max Game

## 1. Problem Details

**Question Link:** https://codeforces.com/problemset/problem/2263/A

**Question Name:** Min Max Game

**Platform:** Codeforces  
**Problem ID:** 2263A  
**Difficulty:** Rating 800  
**Topics:** games  
**Accepted Submission:** Java 21 | Runtime: 265 ms | Memory: 624 KB  
**Submission Link:** https://codeforces.com/problemset/submission/2263/395485240  
**Documented:** 2026-10-21 15:44 UTC

**Question Description:**

```text
A. Min Max Game

time limit per test
1 second

memory limit per test
256 megabytes

input
standard input

output
standard output

Bessie and Elsie are playing a game on a binary array $$$a$$$ of length $$$n$$$.

The players alternate turns, with Bessie moving first. On Bessie's turn, she chooses two adjacent elements $$$x$$$ and $$$y$$$ and replaces them with the single value $$$\max(x,y)$$$.

On Elsie's turn, she chooses two adjacent elements $$$x$$$ and $$$y$$$ and replaces them with the single value $$$\min(x,y)$$$.

After each move, the length of the array decreases by $$$1$$$. The game ends when only one element remains. Bessie wins if the final element is $$$1$$$, and Elsie wins if the final element is $$$0$$$.

Assuming both players play optimally, determine who wins.

Input

Each test contains multiple test cases. The first line contains the number of test cases $$$t$$$ ($$$1 \le t \le 500$$$). The description of the test cases follows.

The first line of each test case contains a single integer $$$n$$$ ($$$2 \leq n \leq 100$$$).

The second line of each test case contains $$$n$$$ integers $$$a_1, a_2, \ldots, a_n$$$ ($$$0 \leq a_i \leq 1$$$).

Output

For each test case, you should output the name of who wins on a new line.

Example

Input

3

5

1 0 1 0 1

3

0 0 1

4

1 1 0 0

Output

Bessie

Elsie

Bessie

Note

For the first test case, Bessie can guarantee a win. One possible game is as follows: $$$$$$ [\color{red}{1},\color{red}{0},1,0,1] \to [1,\color{red}{1},\color{red}{0},1] \to [\color{red}{1},\color{red}{0},1] \to [\color{red}{1},\color{red}{1}] \to [1]. $$$$$$ The final value is $$$1$$$, so Bessie wins (the red highlight denotes the two adjacent elements picked on that turn).

For the second test case, no matter which move Bessie makes, Elsie can make the final value $$$0$$$. Therefore, Elsie wins.

For the third test case, one possible winning game for Bessie is: $$$$$$ [1,\color{red}{1},\color{red}{0},0] \to [1,\color{red}{1},\color{red}{0}] \to [\color{red}{1},\color{red}{0}] \to [1]. $$$$$$ The final value is $$$1$$$, so Bessie wins.
```

*Problem text as provided by Codeforces, converted to plain text.*

## 2. Test Cases

Not generated. No AI provider is configured, so only your accepted solution is included. Add one in Settings and choose "Generate AI docs" to enrich this file.

## 3. Approach

Not generated. No AI provider is configured, so only your accepted solution is included. Add one in Settings and choose "Generate AI docs" to enrich this file.

## 4. Java Solution

### Original Accepted Submission

> Your code as submitted and accepted on Codeforces (265 ms, 624 KB).

```java
import java.math.*;
import java.util.*;
public class Solution {
    public static void main(String[] args)
    {
        Scanner sc=new Scanner(System.in);
        int t=sc.nextInt();
        while(t-->0)
        {
            Map<Integer,Integer> m1=new HashMap<>();
            int n=sc.nextInt();
            int [] arr=new int[n];
            for(int i=0;i<n;i++)
            {
                arr[i]=sc.nextInt();
                m1.put(arr[i],m1.getOrDefault(arr[i],0)+1);
            }

            int zero=m1.getOrDefault(0,0);
            int one=m1.getOrDefault(1,0);
//            System.out.println(zero+" "+one);
            if(zero>one)
            {
                System.out.println("Elsie");
            }
            else {
                System.out.println("Bessie");
            }

        }
    }
}
```

## 5. Motivation

*Every problem you solve strengthens the way you think.*

<div align="center">

## Thank You 🚀

</div>
