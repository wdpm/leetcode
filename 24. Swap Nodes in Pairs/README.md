# 24. Swap Nodes in Pairs
Given a linked list, swap every two adjacent nodes and return its head.

For example,
Given ``1->2->3->4``, you should return the list as ``2->1->4->3``.

Your algorithm should use only **constant space**. You may not modify the values in the list, **only nodes itself can be changed**.
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
 * @return {ListNode}
 */
var swapPairs = function(head) {

    //https://discuss.leetcode.com/topic/51162/simple-0ms-c-solution-beats-98-08
    if(head===null||head.next===null){
        return head;
    }
    
    var dummy=new ListNode(0);
    dummy.next=head;
    var prev=dummy;
    while(head && head.next){
        var tmp=head.next.next;//step 1: save a copy of head.next.next
        // console.log(head.next.next.val);//Line 24: TypeError: Cannot read property 'val' of null
        prev.next=head.next;//step 2:
        head.next.next=head;//step 3: let head.next.next point to head
        head.next=tmp;//step 4: change head.next to tmp
        
        //for next iteration
        prev=head;
        head=tmp;
    }
    
    return dummy.next;
    
};
```