# 283. Move Zeroes
Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].

>Note:
- You must do this in-place without making a copy of the array.
- Minimize the total number of operations.
``` js
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
    var index=0;
    
    if(nums.length>1){
        //数组长度大于1
        for(var i=0;i<nums.length;i++){
            
            //如果当前位置不为0
            if(nums[i]!==0){
                //把该值赋值到前面为0的位置
                nums[index]=nums[i];
                //该值(原来不为0)的位置赋值为0,如果index==i，表明两个指针重合，该位置不必置0
                if(index!=i){
                  nums[i]=0; 
                }
                //指针向右移动
                index++;
            }
            
            //当前位置为0, i++
        }
    }
    
};
```