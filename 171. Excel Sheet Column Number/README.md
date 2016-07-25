# 171. Excel Sheet Column Number
Related to question Excel Sheet Column Title

Given a column title as appear in an Excel sheet, return its corresponding column number.

For example:
```
    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28
```
``` js
/**
 * 处理26进制
 * @param {string} s
 * @return {number}
 */
var titleToNumber = function(s) {
    var ret=0;
    for(var i=0;i<s.length;i++){
       //例如AB
       //ret=0*26+'A'-'A'+1=0+1=1;
       //ret=1*26+'B'-'A'+1=26+2=28;
       ret=ret*26+(s.charCodeAt(i)-65+1);
    }
    return ret;
};
```