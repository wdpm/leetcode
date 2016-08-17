# 107. Binary Tree Level Order Traversal II
Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).

For example:
Given binary tree ``[3,9,20,null,null,15,7]``,
```
    3
   / \
  9  20
    /  \
   15   7
```
return its bottom-up level order traversal as:
```
[
  [15,7],
  [9,20],
  [3]
]
```
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
 * @return {number[][]}
 */
var levelOrderBottom = function(root) {
    var ret=[];
    dfs(root,ret,0);
    return ret;
    
    function dfs(root,res,level){
        if(root===null){
            return;
        }
        
        if(res.length===level){
            res.unshift([]);
        }
        
        res[res.length-level-1].push(root.val);
        
        //recursive
        dfs(root.left,res,level+1);
        dfs(root.right,res,level+1);
    }
    
    return ret;   
};
```