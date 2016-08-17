# 118. Pascal's Triangle
Given numRows, generate the first numRows of Pascal's triangle.

For example, given numRows = 5,
Return
```
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```
## Solution1
``` js
/**
 * @param {number} numRows
 * @return {number[][]}
 */
var generate = function(numRows) {
    
    if(numRows===0){
        return [];
    }
    
    if(numRows==1){
       return [[1]] ;
    }
    
    if(numRows==2){
        return[[1],[1,1]];
    }
    
    //numRows>=3
    var ret=[];
    ret[1]=[1];
    ret[2]=[1,1]
    for(var i=3;i<=numRows;i++){
        ret[i]=[];
        ret[i].push(1);
        //ret[i-1].length-1 times loop
        for(var j=0,len=ret[i-1].length-1 ;j<len;j++){
            var sum=ret[i-1][j]+ret[i-1][j+1];
            ret[i].push(sum);
        }
        ret[i].push(1);
    }
    
    return ret.slice(1);   
};
```