# 1. Two Sum
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution.

Example:
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
``` js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    var hash={};
    for(var i=0;i<nums.length;i++){
        //数组元素的值为name,数组坐标为value
        hash[nums[i]]=i;
    }
    
    // console.log(hash);
    for(var j=0;j<nums.length;j++){
        var first=nums[j];
        var second=target-first;
        if(hash.hasOwnProperty(second)&&hash[second]!==j){
            return [j,hash[second]];
        }
    }
};
```