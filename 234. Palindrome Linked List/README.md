# 234. Palindrome Linked List
Given a singly linked list, determine if it is a palindrome.

**Follow up**:

Could you do it in O(n) time and O(1) space?
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
var isPalindrome = function(head) {
    //reference: https://discuss.leetcode.com/topic/27605/my-easy-understand-c-solution
    var temp=head;
    return check(head);
    
    function check(p){
        if(p===null) return true;
        var isPal=check(p.next) &&(temp.val===p.val);
        temp=temp.next;
        // console.log(temp);
        return isPal;
    }
};
```

## Solution2
1. let a dummy pointer points to the middle of linked list
2. reverse two parts
3. judge whether is equal