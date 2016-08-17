# 189. Rotate Array
Rotate an array of n elements to the right by k steps.

For example, with n = 7 and k = 3, the array ``[1,2,3,4,5,6,7]`` is rotated to ``[5,6,7,1,2,3,4]``.

**Note**:
Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.

**Hint**:
Could you do it in-place with O(1) extra space?
## Solution1
``` js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var rotate = function(nums, k) {
    //https://leetcode.com/articles/rotate-array/
    //solution 2: reverse array three times
    //for example:[1,2,3,4,5,6,7]
    //step 1:reverse all elements:[7,6,5,4,3,2,1]
    //step 2:reverse the first k elements:[5,6,7,...]
    //step 3:reverse the last n-k elements:[...,1,2,3,4]
    
    //mod
    k=k%nums.length;
    reverse(nums,0,nums.length-1);
    reverse(nums,0,k-1);
    reverse(nums,k,nums.length-1);
    
    function reverse(nums,start,end){
        while(start<end){
            var tmp=nums[start];
            nums[start]=nums[end];
            nums[end]=tmp;
            start++;
            end--;
        }
    }
    
    //complexity analysis
    //time:O(n).n elements are reversed a total of three times.[译:三次翻转，一共是n/2+k/2+(n-k)/2=n]
    //space:O(1).No extra space  is used.
};
```