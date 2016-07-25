# 100. Same Tree
Given two binary trees, write a function to check if they are equal or not.

Two binary trees are considered equal if they are structurally identical and the nodes have the same value.
``` js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {boolean}
 */
var isSameTree = function(p, q) {
    //相应位置两个节点一个为null，一个不为null，代表不等
    if(p===null && q!==null){
        return false;
    }
    //相应位置两个节点一个为null，一个不为null，代表不等
    if(p!==null&&q===null){
        return false;
    }
    
    //相应位置两个节点都为null，代表相等
    if(p===null &&q===null){
        return true;
    }
    
    //相应位置两个节点都不为null，那么比较它们的值
    if(p!==null && q!==null){
        //值不等，代表不等
        if(p.val!==q.val){
            return false; 
        }
        //值相等，递归左右子树
        else{
            return isSameTree(p.left,q.left) && isSameTree(p.right,q.right);
        }
    }
    
};
```