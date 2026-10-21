# Add Two Numbers

## 1. Problem Details

**Question Link:** https://leetcode.com/problems/add-two-numbers/

**Question Name:** Add Two Numbers

**Platform:** LeetCode  
**Problem ID:** 2  
**Difficulty:** Medium  
**Topics:** Linked List, Math, Recursion  
**Accepted Submission:** Java | Runtime: 3 ms | Memory: 45.9 MB | 2026-10-21 13:16 UTC  
**Submission Link:** https://leetcode.com/submissions/detail/2177963569/  
**Documented:** 2026-10-21 13:17 UTC

**Question Description:**

```text
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Example 1:

[image]

Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.

Example 2:

Input: l1 = [0], l2 = [0]
Output: [0]

Example 3:

Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]

Constraints:

- The number of nodes in each linked list is in the range [1, 100].

- 0 <= Node.val <= 9

- It is guaranteed that the list represents a number that does not have leading zeros.
```

*Problem text as provided by LeetCode, converted to plain text.*

## 2. Test Cases

Not generated. No AI provider is configured, so only your accepted solution is included. Add one in Settings and choose "Generate AI docs" to enrich this file.

## 3. Approach

Not generated. No AI provider is configured, so only your accepted solution is included. Add one in Settings and choose "Generate AI docs" to enrich this file.

## 4. Java Solution

### Original Accepted Submission

> Your code as submitted and accepted on LeetCode (3 ms, 45.9 MB).

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {

    // public ListNode reverse(ListNode head)
    // {
    //     if(head==null)
    //     {
    //         return null;
    //     }
    //     ListNode prev=null;
    //     ListNode curr=head;
    //     ListNode next=null;
    //     while(curr!=null)
    //     {
    //         next=curr.next;
    //         curr.next=prev;
    //         prev=curr;
    //         curr=next;
    //     }
    //     return head;
    // }
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode curr1=l1;
        ListNode curr2=l2;
        ListNode dummy=new ListNode(-1);
        ListNode ans=dummy;
        int c=0;
        while(curr1!=null || curr2!=null)
        {
            int x=curr1!=null?curr1.val:0;
            int y=curr2!=null?curr2.val:0;

            if(curr1!=null)
            {
                curr1=curr1.next;
            }
            if(curr2!=null)
            {
                curr2=curr2.next;
            }
            int z=(x+y+c)%10;
            c=(x+y+c)/10;

            ListNode newNode=new ListNode(z);
            dummy.next=newNode;
            dummy=dummy.next;
        }

        if(c>0)
        {
            ListNode newNode=new ListNode(c);
            dummy.next=newNode;
            dummy=dummy.next;
        }
        return ans.next;
    }
}
```

## 5. Motivation

*Every problem you solve strengthens the way you think.*

<div align="center">

## Thank You 🚀

</div>
