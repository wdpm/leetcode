# 326. Power of Three
Given an integer, write a function to determine if it is a power of three.
``` js
/**
 * @param {number} n
 * @return {boolean}
 */
var isPowerOfThree = function(n) {
    if(n%2===0){
        return false;
    }
    
    while(n%3===0){
        n=n/3;
    }
    
    return n===1;
};
```
