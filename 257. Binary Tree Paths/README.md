# 257. Binary Tree Paths
Given a binary tree, return all root-to-leaf paths.

For example, given the following binary tree:
```
   1
 /   \
2     3
 \
  5
```
All root-to-leaf paths are:
```
["1->2->5", "1->3"]
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
 * @return {string[]}
 */
var binaryTreePaths = function(root) {
    var ret=[];
    var path=[];
    traverse(root);
    return ret;
    
    function traverse(root){
        if(!root){
            return;
        }
        
        //root is not null,add to path
        path.push(root.val);
        
        //leaf
        if(!root.left&&!root.right){
           ret.push(path.join('->')) ;
        }else{
           traverse(root.left); 
           traverse(root.right);
        }
        
        // console.log("before pop: "+path);
        //remember to pop ele:leaf------->root
        path.pop();
        // console.log("after pop: "+path);
        
    }
};
```
