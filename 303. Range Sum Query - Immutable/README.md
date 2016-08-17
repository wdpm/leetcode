# 303. Range Sum Query - Immutable
Given an integer array nums, find the sum of the elements between indices i and j (i ≤ j), inclusive.

**Example**:
```
Given nums = [-2, 0, 3, -5, 2, -1]

sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3
```
**Note**:
1. You may assume that the array does not change.
2. There are many calls to sumRange function.

## ~~Solution1~~
``` js
/**
 * @constructor
 * @param {number[]} nums
 */
var NumArray = function(nums) {
    this.arr=nums;
};

/**
 * @param {number} i
 * @param {number} j
 * @return {number}
 */
NumArray.prototype.sumRange = function(i, j) {
    //Time Limit Exceeded
    var a=this.arr;
    var start=i;
    var end=j;
    var res=0;
    for( ; start <= end ; start++){
        res+=a[start];
    }
    return res;
};


/**
 * Your NumArray object will be instantiated and called as such:
 * var numArray = new NumArray(nums);
 * numArray.sumRange(0, 1);
 * numArray.sumRange(0, 2);
 */
```
 
## Solution2
``` js
/**
 * @constructor
 * @param {number[]} nums
 */
var NumArray = function(nums) {
    var sum=[];
    sum[0]=0;
    for(var i=1;i<=nums.length;i++){
        sum[i]=sum[i-1]+nums[i-1];
    }
    this.sum=sum;
};

/**
 * @param {number} i
 * @param {number} j
 * @return {number}
 */
NumArray.prototype.sumRange = function(i, j) {
    var sum=this.sum;
    return sum[j+1]-sum[i];
};


/**
 * Your NumArray object will be instantiated and called as such:
 * var numArray = new NumArray(nums);
 * numArray.sumRange(0, 1);
 * numArray.sumRange(0, 2);
 */
```
 