# 350. Intersection of Two Arrays II
Given two arrays, write a function to compute their intersection.

Example:
Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2, 2].

Note:
- Each element in the result should appear as many times as it shows in both arrays.
- The result can be in any order.
``` java
public class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        //这道题的第一版不允许重复元素，使用了set
        //这里允许重复元素，那么使用list
        
        //存放nums1
        List<Integer> list1=new ArrayList<>();
        //临时存放中间结果
        List<Integer> tempList=new ArrayList<>();
        
        //将nums1复制到list1
        for(int item:nums1){
            list1.add(item);
        }
        
        //遍历nums2
        for(int i=0;i<nums2.length;i++){
            if(list1.contains(nums2[i])){
                //将交集元素存放到tempList
                tempList.add(nums2[i]);
                //在list1中找到相同元素的索引，删除它
                list1.remove(list1.indexOf(nums2[i]));
            }
        }
        
        //将tempList复制到res数组
        int index=0;
        int[] res=new int[tempList.size()];
        for(int item:tempList){
            res[index++]=item;
        }
        
        return res;
    }
}
```