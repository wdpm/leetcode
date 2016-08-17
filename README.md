# leetcode
Recording my solution about leetcode.
Most language is JavaScript,with very small part is Java.

## Stage-1 
- Finish easy level at 2016/8/16.
- 81 / 385 questions solved.

## Feelings of Stage-1:

- 1. Easy level focus on AC result, not very concerned about time complexity and space complexity.This means my some solutions maybe used Burte-Force thought.Some problem inspects divide-and-conquer, recursion, Reduce and Conquer Method(e.g. binary divide), simple dynamic programming(dp).
- 2. Basic data structure: Array, Stack, Tree, Map, Set.
- 3. Easy level covers following aspects:
    - String 
      - some implementations of built-in functions.For example,``indexOf()``, ``parseInt()/parseFloat()`` ,etc.
      - insert, delete, update, query
    - Array 
      - basic operation about built-in function.``indexOf``, ``lastIndexOf()``, ``push()``, ``pop()``, ``sort``, ``slice``,``forEach()``,
        ``concat()``, ``join()``, ``reverse()``, ``shift()``, ``unshift()``, ``splice()`` 
    - Set 
      - use its Non-repetitive nature to remove duplicate.For example, pass parameters to its constructor like ``var set = new Set(nums);``
    - Map 
      - use hash to save/cache key-values items.It is very helpful in some problem if I want to built some mapping relation of strings.
    - Stack
      - baisc operation such as ``push``, ``pop``, ``peek``, ``size()``, ``isEmpty()``.
      - use stack to check whether parentheses is valid.
    - linked list
      - basic operation such as: query a certain node's value, remove/insert/update a node(maybe can't change node's value, only node itself can be changed)
      - reverse and its derivation
    - Tree
      - a large part of the easy level problems are related to tree.Tree traversal(inOrder,preOrder,postOrder),the depth of tree,BST related(to find a certain value).
      - many solutions are recursive for code clean,but its efficiency sometimes will be slower than iteration(e.g. fibonacci sequence)
