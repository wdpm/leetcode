# 198. House Robber
You are a professional robber planning to rob houses along a street. 
Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that 
adjacent houses have security system connected and **it will automatically contact the police if two adjacent houses were broken into on the same night.**

Given a list of non-negative integers representing the amount of money of each house, 
determine the maximum amount of money you can rob tonight **without alerting the police.**
## Solution1
``` js
/**
 * @param {number[]} nums
 * @return {number}
 */
var rob = function(nums) {
    //nums: non-negative integers 
    //dp problem
    //use odd and even index to divide
    var oddSum=0;
    var evenSum=0;
    for(var i=0,len=nums.length;i<len;i++){
        //even index
        if(i%2===0){
           evenSum=Math.max(evenSum+nums[i],oddSum);
        }else{
        //odd index
           oddSum=Math.max(oddSum+nums[i],evenSum);
        }
    }
    
    return Math.max(evenSum,oddSum);
};
```
