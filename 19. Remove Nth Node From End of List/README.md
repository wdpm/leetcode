# 19. Remove Nth Node From End of List
Given a linked list, remove the nth node from the end of list and return its head.

For example,
```
   Given linked list: 1->2->3->4->5, and n = 2.

   After removing the second node from the end, the linked list becomes 1->2->3->5.
```
**Note**:
Given n will always be valid.
Try to do this in one pass.

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
 * @param {number} n
 * @return {ListNode}
 */
var removeNthFromEnd = function(head, n) {
    //case 1:
    //1->2->null, n=2
    //find=null(find.next=null),use head=head.next to remove 1
    
    //case 2:
    //1->2->3->null, n=2
    //find=3,find.next=null,use head.next=head.next.next to remove 2
    
    //case 3:
    //1->2->3->4->null, n=2
    //find=3,find.next=4,use recursion to 2->3->4->null,that mean call ``removeNthFromEnd(head.next, n)``
    
    //
    if(head===null){
        return head;
    }
    
    var find=head;
    //get find and find.next
    for(var i=0;i<n;i++){
        find=find.next;
    }
    
    if(find===null){//case 1
        head=head.next;
    }else if(find.next===null){//case 2
        head.next=head.next.next;
    }else{//case 3
        removeNthFromEnd(head.next,n);
    }
    
    return head;
};
```