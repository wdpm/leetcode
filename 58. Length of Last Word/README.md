# 58. Length of Last Word
Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string.

If the last word does not exist, return 0.

**Note**: A word is defined as a character sequence consists of non-space characters only.

For example, 
Given s = ``"Hello World"``,
return ``5``.
## Solution1
``` js
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLastWord = function(s) {
    if(s.trim().length===0){
        return 0;
    }
    var a=s.split(' ');
    // console.log(a);
    var index=a.length-1;
    while(a[index]===""){
        index--;
    }
    return a[index].length;
};
```