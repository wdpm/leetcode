# 226. Invert Binary Tree
Invert a binary tree.
```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```
to
```
     4
   /   \
  7     2
 / \   / \
9   6 3   1
```
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
 * @return {TreeNode}
 */
var invertTree = function(root) {
    //当root不为空时需要反转
    if(root!==null){
        var temp=root.left;
        //递归右子树-->左子树
        root.left=invertTree(root.right);
        //递归左子树-->右子树
        root.right=invertTree(temp);
    }
    //root为空时，返回null
    return root;
};
```