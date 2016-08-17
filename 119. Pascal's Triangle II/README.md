# 119. Pascal's Triangle II
Given an index k, return the kth row of the Pascal's triangle.

For example, given k = 3,
Return ``[1,3,3,1]``.

**Note**:
Could you optimize your algorithm to use only O(k) extra space?
## Solution1
``` js
/**
 * @param {number} rowIndex
 * @return {number[]}
 */
var getRow = function(rowIndex) {
    if(rowIndex===0){
        return [1];
    }
    
    if(rowIndex===1){
        return [1,1];
    }
    
    var ret=[];
    ret[0]=[1];
    ret[1]=[1,1];
    for(var i=2;i<=rowIndex;i++){
        ret[i]=[];
        ret[i].push(1);
        //deal with center digits
        for(var j=0;j<ret[i-1].length-1;j++){
            var sum=ret[i-1][j]+ret[i-1][j+1];
            ret[i].push(sum);
        }
        ret[i].push(1);
    }
    
    return ret[rowIndex];
    
};
```