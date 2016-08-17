# 26. Remove Duplicates from Sorted Array
Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this in place with constant memory.

For example,
Given input array nums = ``[1,1,2]``,

Your function should return length = ``2``, with the first two elements of nums being ``1`` and ``2`` respectively. It doesn't matter what you leave beyond the new length.
## Solution1
``` js
/**
 * @param {number[]} nums
 * @return {number}
 */
var removeDuplicates = function(nums) {
    //method1:two pointers
    //pointer1 marks a index 
    //pointer2 for loop traverse
    var index=1;
    for(var i=0,len=nums.length;i<len-1;i++){
        //adjacent elements are not equal
        if(nums[i]!==nums[i+1]){
            nums[index++]=nums[i+1];
        }
        //adjacent elements are equal, do nothing
    }
    
    nums=nums.slice(0,index);
    return index;  
};
```