# A Very Big Sum

## 1. Problem Details

**Question Link:** https://www.hackerrank.com/challenges/a-very-big-sum/problem

**Question Name:** A Very Big Sum

**Platform:** HackerRank  
**Problem ID:** a-very-big-sum  
**Documented:** 2026-10-21 15:04 UTC

**Question Description:**

```text
[image: HackerRank Logo]

|

- Prepare
- Algorithms
- Warmup
- A Very Big Sum

Exit Full Screen View

- Problem
- Submissions
- Leaderboard
- Discussions
- Editorial

In this challenge, you need to calculate and print the sum of elements in an array, considering that some integers may be very large.

Function Description

Complete the  function with the following parameter(s):

- : an array of integers

Return

- : the sum of the array elements

Input Format

The first line of the input consists of an integer .

The next line contains  space-separated integers contained in the array.

Output Format

Return the integer sum of the elements in the array.

Constraints

Sample Input

STDIN                                                   Function
-----                                                   --------
5                                                       arr[] size n = 5
1000000001 1000000002 1000000003 1000000004 1000000005  arr[...]

Output

5000000015

Note:

The range of the 32-bit integer is .

When we add several integer values, the resulting sum might exceed the above range. You might need to use long int C/C++/Java to store such sums.

Change Theme

Language

Java 15

More

33

34

35

36

37

38

39

40

41

42

43

44

45

46

47

48

49

50

51

52

53

54

public class Solution {

    public static void main(String[] args) throws IOException {

        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader

        (System.in));

        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.

        getenv("OUTPUT_PATH")));

        int arCount = Integer.parseInt(bufferedReader.readLine().trim());

        List<Long> ar = Stream.of(bufferedReader.readLine().replaceAll("\\s+$", "").

        split(" "))

            .map(Long::parseLong)

            .collect(toList());

        long result = Result.aVeryBigSum(ar);

        bufferedWriter.write(String.valueOf(result));

        bufferedWriter.newLine();

        bufferedReader.close();

        bufferedWriter.close();

    }

}

Line: 54 Col: 1

Submit Code

Run Code

Upload Code as File

Test against custom input

Congratulations

You solved this challenge. Would you like to challenge your friends?
Share on XShare on LinkedIn

Next Challenge

Test case 0

Test case 1

Compiler Message

Success

Input (stdin)
Download

-
5

-
1000000001 1000000002 1000000003 1000000004 1000000005

Expected Output
Download

-
5000000015
```

*Problem text as provided by HackerRank, converted to plain text.*

## 2. Test Cases

Not generated. No AI provider is configured, so only your accepted solution is included. Add one in Settings and choose "Generate AI docs" to enrich this file.

## 3. Approach

Not generated. No AI provider is configured, so only your accepted solution is included. Add one in Settings and choose "Generate AI docs" to enrich this file.

## 4. Original Solution (unknown)

### Original Accepted Submission

> Your code as submitted and accepted on HackerRank.

```
        bufferedWriter.newLine();

        bufferedReader.close();
        bufferedWriter.close();
    }
}
```

## 5. Motivation

*Every problem you solve strengthens the way you think.*

<div align="center">

## Thank You 🚀

</div>
