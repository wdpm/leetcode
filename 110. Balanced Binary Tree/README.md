# 110. Balanced Binary Tree
Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.
``` js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * 平衡二叉树的定义:
 * 它是一棵空树或它的左右两个子树的高度差的绝对值不超过1，并且左右两个子树都是一棵平衡二叉树
 * @param {TreeNode} root
 * @return {boolean}
 */
var isBalanced = function(root) {
    //根节点为空,为平衡二叉树
    if(root===null){
        return true;
    }
    //根节点左右子树都为空，为平衡二叉树
    if(root.left===null && root.right===null){
        return true;
    }
    //如果根节点左右子树高度差大于1，不为平衡二叉树
    if(Math.abs(depth(root.left)-depth(root.right))>1){
        return false;
    }
    
    //如果根节点左右子树高度差小于等于1，那么递归左右子树来计算是否平衡
    return isBalanced(root.left) && isBalanced(root.right);
    
    //计算以某节点为根的树的最大高度
    function depth(root){
        if(root===null){
            return 0;
        }
        //递归以某节点为根的树的左右子树
        return 1+Math.max(depth(root.left),depth(root.right));
    }
};
```