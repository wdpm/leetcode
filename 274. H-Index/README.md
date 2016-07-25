# 274. H-Index
Given an array of citations (each citation is a non-negative integer) of a researcher, write a function to compute the researcher's h-index.

According to the definition of h-index on Wikipedia: "A scientist has index h if h of his/her N papers have at least h citations each, and the other N − h papers have no more than h citations each."

For example, given citations = [3, 0, 6, 1, 5], which means the researcher has 5 papers in total and each of them had received 3, 0, 6, 1, 5 citations respectively. Since the researcher has 3 papers with at least 3 citations each and the remaining two with no more than 3 citations each, his h-index is 3.

Note: If there are several possible values for h, the maximum one is taken as the h-index.

Hint:
- An easy approach is to sort the array first.
- What are the possible values of h-index?
- A faster approach is to use extra space.
``` js
/**
 * @param {number[]} citations
 * @return {number}
 */
var hIndex = function(citations) {
    //在数组中找到一个数字H，使得数组中至少有H个数字大于等于H，其余的数字小于等于H
    
    //升序排序
    citations.sort(function(a,b){
        return a-b;
    });
    
    // console.log(citations);
    for(var i=0;i<citations.length;i++){
        if(citations.length-i<=citations[i]){
            return  citations.length-i;
        }
    }
    return 0;
};
```