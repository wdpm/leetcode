# 9. Palindrome Number
Determine whether an integer is a palindrome. Do this without extra space.
``` js
/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function(x) {
    //Do this without extra space
    //那就只能O(1)空间复杂度
    
    if(x===0){
        return true;
    }
    //为负数，或者为10的倍数，都不是回文数
    if(x<0 || x%10===0){
        return false;
    }
    var copyX=x;
    var ret=0;
    while(x){
        ret=ret*10+x%10;
        x=parseInt(x/10);
    }
    // console.log(ret);
    return copyX===ret;
};
```