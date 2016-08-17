# 101. Symmetric Tree
Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

For example, this binary tree ``[1,2,2,3,4,4,3]`` is symmetric:
```
    1
   / \
  2   2
 / \ / \
3  4 4  3
```
But the following ``[1,2,2,null,3,null,3]`` is not:
```
    1
   / \
  2   2
   \   \
   3    3
```
**Note**:
Bonus points if you could solve it both recursively and iteratively.

## Solution1
- recursively
``` js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {boolean}
 */
var isSymmetric = function(root) {
    
    if(!root){
        return true;
    }
    
    function recursiveCheck(left,right){
        if(left===null&&right===null){
            return true;
        }
        if(left===null^right===null){
            return false;
        }
        //left and right both are not null
        if(left.val===right.val){
            return true && recursiveCheck(left.left,right.right) && recursiveCheck(left.right,right.left);
        }else{
            return false;
        }
    }
    
    return recursiveCheck(root.left,root.right); 
};
```