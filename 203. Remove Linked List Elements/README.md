# 203. Remove Linked List Elements
Remove all elements from a linked list of integers that have value val.

**Example**

Given: ``1 --> 2 --> 6 --> 3 --> 4 --> 5 --> 6``, ``val = 6``

Return: ``1 --> 2 --> 3 --> 4 --> 5``

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
 * @param {number} val
 * @return {ListNode}
 */
var removeElements = function(head, val) {
    //set a prev node, let prev.next=head.
    var prev=new ListNode();
    prev.next=head;
    var cur=prev;
    while(cur.next!==null){
        if(cur.next.val==val){
            cur.next=cur.next.next;
        }else{//!==
            cur=cur.next;
        }
    }
    
    // console.log(prev);
    return prev.next;
};
```