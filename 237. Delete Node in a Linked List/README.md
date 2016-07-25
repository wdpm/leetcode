# 237. Delete Node in a Linked List
Write a function to delete a node (except the tail) in a singly linked list, given only access to that node.

Supposed the linked list is 1 -> 2 -> 3 -> 4 and you are given the third node with value 3, the linked list should become 1 -> 2 -> 4 after calling your function.
``` js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} node
 * @return {void} Do not return anything, modify node in-place instead.
 */
var deleteNode = function(node) {
    //题目限制了对节点的访问：只能访问当前节点，那么就不能通过它的前继节点来删除它了。只能访问它的后继结点
    //思路：将node的后继节点的值赋值给node，将node的后继指针修改为node的后继结点的后继结点(等于删除node的后继节点)。
    if(node.next!==null){
        node.val=node.next.val;
        node.next=node.next.next;
    }
    
}
```