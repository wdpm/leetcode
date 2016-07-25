# 342. Power of Four
Given an integer (signed 32 bits), write a function to check whether it is a power of 4.

Example:
Given num = 16, return true. Given num = 5, return false.
``` js
/**
 * @param {number} num
 * @return {boolean}
 */
var isPowerOfFour = function(num) {
    
    //1=4^0
    if(num===1){
        return true;
    }

    //
    if(num%4!==0 ||num===0){
        return false;
    }
    
    while(num%4===0){
        num=num>>2;
    }
    
    return num==1;
};
```