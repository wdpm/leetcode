# 349. Intersection of Two Arrays
Given two arrays, write a function to compute their intersection.

Example:
Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2].

Note:
- Each element in the result must be unique.
- The result can be in any order.
``` js
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersection = function(nums1, nums2) {
    var set1=new Set();
    var set2=new Set();
    var res=[];
    
    for(var i=0;i<nums1.length;i++){
        set1.add(nums1[i]);
    }
    
    for(var j=0;j<nums2.length;j++){
        set2.add(nums2[j]);
    }
    
    //遍历set1,
    set1.forEach(function(item,sameItem,set1){
       //如果set2中含有这个元素，添加到结果数组
       if(set2.has(item)) {
           res.push(item);
       }
    });  

    return res;
    
};
```