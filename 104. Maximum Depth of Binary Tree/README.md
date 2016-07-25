# 104. Maximum Depth of Binary Tree
Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.
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
 * @return {number}
 */
var maxDepth = function(root) {
    //use === instead of ==
    if(root===null){
        return 0;
    }
    //递归算法，分别求出根节点左子树、右子树的深度
    //二叉树最长深度=最大值+1
    return 1+Math.max(maxDepth(root.left),maxDepth(root.right));
};
```