# 168. Excel Sheet Column Title
Given a positive integer, return its corresponding column title as appear in an Excel sheet.

For example:
```
    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 
```
## Solution1
``` js
/**
 * @param {number} n
 * @return {string}
 */
var convertToTitle = function(n) {
    //for example:AB
    //AB=26+2;
    var res="";
    while(n){
        res=String.fromCharCode((n-1)%26+65)+res;
        n=parseInt((n-1)/26,10);
    }

    return res;
};
``