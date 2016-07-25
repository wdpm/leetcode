# 371. Sum of Two Integers
Calculate the sum of two integers a and b, but you are not allowed to use the operator + and -.

Example:
Given a = 1 and b = 2, return 3.
``` js
/**
 * @param {number} a
 * @param {number} b
 * @return {number}
 */
var getSum = function(a, b) {
    if(a===0){
        return b;
    }
    
    if(b===0){
        return a;
    }
    
    return getSum(a^b,(a&b)<<1);
};
```
