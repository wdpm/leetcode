# 21. Merge Two Sorted Lists
Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.
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
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var mergeTwoLists = function(l1, l2) {
    if(l1===null){
        return l2;
    }
    
    if(l2===null){
        return l1;
    }
    
    if(l1.val<l2.val){
        l1.next=mergeTwoLists(l1.next,l2);
        return l1;
    }else{
        l2.next=mergeTwoLists(l1,l2.next);
        return l2;
    }
};
```

## Solution2
> too much similar to merge sort
``` js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var mergeTwoLists = function(l1, l2) {
    var node=new ListNode(0);
    var prev=node;
    //比较
    while(l1!==null&&l2!==null){
        if(l1.val<l2.val){
            prev.next=l1;
            l1=l1.next;
        }else{
            prev.next=l2;
            l2=l2.next;
        }
        prev=prev.next;
    }
    
    if(l1!==null){
        prev.next=l1;
    }
    
    if(l2!==null){
        prev.next=l2;
    }
    
    return node.next;

};
```