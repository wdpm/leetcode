# 205. Isomorphic Strings
Given two strings **s** and **t**, determine if they are isomorphic.

Two strings are isomorphic if the characters in **s** can be replaced to get **t**.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character but a character may map to itself.

For example,
Given ``"egg"``, ``"add"``, return true.

Given ``"foo"``, ``"bar"``, return false.

Given ``"paper"``, ``"title"``, return true.

**Note**:
You may assume both **s** and **t** have the same length.
## Solution1
``` js
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isIsomorphic = function(s, t) {
    //refercence: https://discuss.leetcode.com/topic/12981/my-6-lines-solution
    var arrS=[].fill(0);
    var arrT=[].fill(0);
    for(var i=0,len=s.length;i<len;i++){
        if(arrS[s[i]]!==arrT[t[i]]){
            return false;
        }else{
            arrS[s[i]]=i+1;
            arrT[t[i]]=i+1;
            // console.log(arrS,arrT);
        }
    }
    
    return true;
};
```

## Solution2
``` js
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isIsomorphic = function(s, t) {
    var mapS=new Map();
    var mapT=new Map();
    var isCan=true;
    
    for(var i=0,len=s.length;i<len;i++){
        if(!mapS[s[i]] && !mapT[t[i]]){
            //相互映射，表示可以替换，即同构
            mapS[s[i]]=t[i];
            mapT[t[i]]=s[i];
        }else if(mapS[s[i]]===t[i]){
            //重复的元素映射关系，跳过
            //例如："foo", "baa" mapS[o]=a在第三次循环中
            continue;
        }else{
            isCan=false;
            break;
            
        }
    }
    
    return isCan;
};
```