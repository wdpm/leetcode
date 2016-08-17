# 160. Intersection of Two Linked Lists
Write a program to find the node at which the intersection of two singly linked lists begins.


For example, the following two linked lists:
```
A:          a1 → a2
                   ↘
                     c1 → c2 → c3
                   ↗            
B:     b1 → b2 → b3
```
begin to intersect at node c1.


**Notes**:

- If the two linked lists have no intersection at all, return ``null``.
- The linked lists must retain their original structure after the function returns.
- You may assume there are no cycles anywhere in the entire linked structure.
- Your code should preferably run in O(n) time and use only O(1) memory.

## Solution1
``` js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */

/**
 * @param {ListNode} headA
 * @param {ListNode} headB
 * @return {ListNode}
 */
var getIntersectionNode = function(headA, headB) {
    //solution 1:
    //step 1: caculate the length of the two linked lists respectively.
    //step 2: in order to use next method to traverse,we should let their begin point equal
    //for example:if len2 > len1,then we should right shift (len2-len1) nodes in linked list2
    
    var len1=0;
    var len2=0;
    var p1=headA;
    var p2=headB;
    
    //step 1
    while(p1!==null){
        p1=p1.next;
        len1++;
    }
    
    while(p2!==null){
        p2=p2.next;
        len2++;
    }
    
    //reset p1 and p2 to their head
    p1=headA;
    p2=headB;
    
    //step 2
    if(len1<len2){
        for(var i=0;i<len2-len1;i++){
            p2=p2.next;
        }
    }else{
        for(var j=0;j<len1-len2;j++){
            p1=p1.next;
        }
    }
    
    while(p1!==p2){
        p1=p1.next;
        p2=p2.next;
    }
    
    return p1;
};
```