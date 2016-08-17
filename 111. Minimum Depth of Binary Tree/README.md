# 111. Minimum Depth of Binary Tree
Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.
## Solution1
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
var minDepth = function(root) {
    if(root===null){
        return 0;
    }
    
    //is leaf
    if(root.left===null&&root.right===null){
        return 1;
    }
    
    if(root.left===null){
        return 1+minDepth(root.right);
    }
    
    if(root.right===null){
        return 1+minDepth(root.left);
    }
    
    //root.left and root.right botn are not null
    return 1+Math.min(minDepth(root.left),minDepth(root.right));
};
```