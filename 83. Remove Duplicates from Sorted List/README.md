# 83. Remove Duplicates from Sorted List
Given a sorted linked list, delete all duplicates such that each element appear only once.

For example,
Given ``1->1->2``, return ``1->2``.

Given ``1->1->2->3->3``, return ``1->2->3``.
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
var deleteDuplicates = function(head) {
    
    //head为空，或者只有head一个节点，直接返回head
    if(head===null||head.next===null){
        return head;
    }
    
    var tmp=head;
    while(tmp!==null&&tmp.next!==null){
        if((tmp.val)===(tmp.next.val)){
            //删除tmp.next节点
            tmp.next=tmp.next.next;
        }else if(tmp.val!==tmp.next.val){
            //指针右移
            tmp=tmp.next;
        }
    }
    
    return head;
    
};
```