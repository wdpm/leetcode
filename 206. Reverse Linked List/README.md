# 206. Reverse Linked List
Reverse a singly linked list.
## Solution1
``` java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev =null;
        while(head!=null){
            ListNode tmp=head.next;
            head.next=prev;
            prev=head;
            head=tmp;
            // System.out.print(prev.val);
        }
        return prev;
    }
}
```

## Solution2
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
var reverseList = function(head) {
    //代码来源：https://discuss.leetcode.com/topic/47023/4-lines-javascript-iteratively
    var prev=null;
    while(head){
        //让head位于prev之前
        //让head下一个节点赋值给head
        //让head赋值给prev
        [head.next,head,prev]=[prev,head.next,head];
        // console.log(prev);
    }
    
    return prev;
};
```
