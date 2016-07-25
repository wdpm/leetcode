# 217. Contains Duplicate
Given an array of integers, find if the array contains any duplicates. Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

## Solution1
``` js
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {
    //解法1：使用传统二重for循环,暴力穷举,时间复杂度O(n^2)
    
    //0个或者1个元素，代表没有重复，返回false
    if(nums.length<=1){
        return false;
    }
    
    for(var i=0;i<nums.length;i++){
        for(var j=i+1;j<nums.length ;j++)
            //有元素相等，代表有重复，返回true
            if(nums[i]==nums[j]){
                return true;
            }
    }
    
    //没有重复，返回fasle
    return false;
};
```

## Solution2
``` js
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) { 
    //解法2： 
     
    //记录数组长度
    var arrLength=nums.length;
    //利用set存放数组
    var set=new Set(nums);
    //比较set的长度和数组长度，如果相同，那么代表没有重复，返回false；反之，返回true
    return set.size!==arrLength;
    
};
```