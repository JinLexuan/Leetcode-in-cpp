# 19. Remove Nth Node From End of List
https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list
Given the head of a linked list, remove the nth node from the end of the list and return its head.



Example 1:  
<img width="555" alt="image" src="https://user-images.githubusercontent.com/60777462/152930521-170f5081-9adc-4796-9ca8-12f1122ec85d.png">

Input: head = [1,2,3,4,5], n = 2  
Output: [1,2,3,5]  

Example 2:  
Input: head = [1], n = 1  
Output: []  

Example 3:  
Input: head = [1,2], n = 1   
Output: [1]  

Constraints:  
The number of nodes in the list is sz.  
1 <= sz <= 30  
0 <= Node.val <= 100  
1 <= n <= sz  

Follow up: Could you do this in one pass?  

``` cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode* dummy=new ListNode(-1);
        dummy->next=head;
        ListNode* fast=dummy, *slow=dummy;
        while(n--) fast=fast->next;
        while(fast->next!=nullptr){
            fast=fast->next;
            slow=slow->next;
        }
        slow->next=slow->next->next;
        return dummy->next;
    }
};
```
