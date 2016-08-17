# 28. Implement strStr()
Implement strStr().

Returns the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.
## Solution1
``` js
/**
 * @param {string} haystack
 * @param {string} needle
 * @return {number}
 */
var strStr = function(haystack, needle) {
    var len1=haystack.length;
    var len2=needle.length;
    if(len2>len1){
        return -1;
    }else if(len2===0){
        return 0;
    }else{
        var threshold=len1-len2;
        for(var i=0;i<=threshold;i++){
            if(haystack.substr(i,len2)===needle){
                return i;
            }
        }
        return -1;
    }
};
```

## ~~Solution2~~
> don't encourage to use built-in function ``indexOf``
``` js
/**
 * @param {string} haystack
 * @param {string} needle
 * @return {number}
 */
var strStr = function(haystack, needle) {
    var len1=haystack.length;
    var len2=needle.length;
    if(len2>len1){
        return -1;
    }else{
        return haystack.indexOf(needle);
    }
};
```