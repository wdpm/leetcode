# 14. Longest Common Prefix
Write a function to find the longest common prefix string amongst an array of strings.

## Solution1
``` js
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function(strs) {
    if(strs.length===0){
        return "";
    }
    
    //let the first string be a standard
    var str1=strs[0];
    if(str1.length===0){
        return "";
    }
    
    //from next string,compare them
    for(var i=1;i<strs.length;i++){
        var str2=strs[i];
        var index=0;
        //``index < str1.length`` avoid ArrayOutOfBound
        while(str1[index]===str2[index]&& index<str1.length){
            index++;
        }
        str1=str1.substr(0,index);
    }
    
    return str1;
};
```