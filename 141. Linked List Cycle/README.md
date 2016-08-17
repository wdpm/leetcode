# 141. Linked List Cycle
Given a linked list, determine if it has a cycle in it.

Follow up:
Can you solve it without using extra space?
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
 * @param {ListNode} head
 * @return {boolean}
 */
var hasCycle = function(head) {
    //two pointers problem.
    //set pointer1 ``p1`` run faster than pointer2 ``p2``.
    //if there is a loop,the ``p1`` must meet with ``p2``
    if(head===null){
        return false;
    }
    var fast=head;
    var slow=head;
    while(fast.next!==null&&fast.next.next!==null){
        fast=fast.next.next;
        slow=slow.next;
        if(fast===slow){
            return true;
        }
    }
    
    return false;
};
```