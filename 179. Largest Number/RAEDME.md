# 179. Largest Number
Given a list of non negative integers, arrange them such that they form the largest number.

For example, given [3, 30, 34, 5, 9], the largest formed number is 9534330.

Note: The result may be very large, so you need to return a string instead of an integer.
``` js
/**
 * @param {number[]} nums
 * @return {string}
 */
var largestNumber = function(nums) {
    
    //为什么不使用return b-a
    //因为在该题目中，3是比30大的
    //假如a=3,b=30,那么ab=330，ba=303，ba-ab为负数
    var sorted=nums.sort(function(a,b){
        var ab=a.toString()+b.toString();
        var ba=b.toString()+a.toString();
        //降序排序
        return ba-ab;
    });
    
    //[0,0]->0
    if(parseInt(sorted)===0){
        return '0';
    }else{
        return sorted.join('');
    }
};
```