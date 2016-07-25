# 169. Majority Element
Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

You may assume that the array is non-empty and the majority element always exist in the array.

## Solution1
``` js
/**
 * 投票问题：超半数者胜出
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
    //解法1：参考https://discuss.leetcode.com/topic/6249/c-solution-o-n-computation-o-1-space-the-problem-can-be-extended-to-n-k-situation
    //投票计算器
    var count=0;
    //候选人，初始为第一个元素
    var candidate=nums[0];
    
    //遍历数组
    for(var i=0;i<nums.length;i++){
        //当票数被削减为0时，重新选择候选人，并置票数为1
        if(count===0){
            candidate=nums[i];
            count=1;
        }
        //当票数不为0,时
        else{//当前元素等于候选人，票数自增
            if(candidate==nums[i]){
                count++;
            }else{//当前元素不等于候选人，票数自减(相当于自身票数被削弱)
                count--;
            }
        }
    }
    
    return candidate;
    
};
```

## Solution2
``` java
public class Solution {
    public int majorityElement(int[] nums) {
        //解法2:时间复杂度O(nlogn),使用java本身的排序算法
        //排序
        Arrays.sort(nums);
        //因为多数元素必定超过一半，那么中间元素肯定就是多数元素
        return nums[nums.length/2];
    }
    
    // //快速排序
    // public void quickSort(int[] a,int l, int r){
    //     if(l<r){
    //         int i=l,j=r,x=a[l];
    //         while(i<j){
    //             while(i<j&&a[j]>=x){
    //                 j--;
    //             }
    //             if(i<j){
    //                 a[i]=a[j];
    //                 i++;
    //             }
                
    //             while(i<j&&a[i]<x){
    //                 i++;
    //             }
    //             if(i<j){
    //                 a[j]=a[i];
    //                 j--;
    //             }
    //         }
    //         //i==j
    //         a[i]=x;
    //         quickSort(a,l,i-1);
    //         quickSort(a,i+1,r);
    //     }
    // }
}
```

## Solution3
``` js
/**
 * 投票问题：超半数者胜出
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
    //解法3：使用js的排序算法
  return nums.sort()[Math.floor(nums.length / 2)];

};
```

## Solution4
``` js
/**
 * 投票问题：超半数者胜出
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
    //解法4：使用hash
    var letterHash={};
    //遍历数组，使用哈希保存出现的次数
    for(var i=0;i<nums.length;i++){
        //如果该哈希已存在，值加1
        if(letterHash[nums[i]]){
            letterHash[nums[i]]+=1;
        }else{//该哈希不存在，值置为1
            letterHash[nums[i]]=1;
        }
    }
    //遍历哈希表
    for(var name in letterHash){
        //找到超半数的项
        if(letterHash[name]>nums.length/2){
            //转化为int类型返回
            return parseInt(name);
        }
    }

};
```