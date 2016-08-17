# 219. Contains Duplicate II
Given an array of integers and an integer k, find out whether there are two distinct indices i and j in the array such that nums[i] = nums[j] and the difference between i and j is at most k.

## Solution1
- direct solution
``` js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {boolean}
 */
var containsNearbyDuplicate = function(nums, k) {
    var len=nums.length;
    for(var i=0;i<len;i++){
        for(var j=i+1;j<len;j++){
            if(nums[i]===nums[j]&&Math.abs(i-j)<=k){
                return true;
            }
        }
    }   
    return false;
};
```

## Solution2
- using map
``` js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {boolean}
 */
var containsNearbyDuplicate = function(nums, k) {
    var map=new Map();
    for(var i=0,len=nums.length;i<len;i++){
        if(map.has(nums[i])){
           if(i-map.get(nums[i])<=k) {
               return true;
           }
        }
        
        map.set(nums[i],i);
    }
    
    return false;
};
```

