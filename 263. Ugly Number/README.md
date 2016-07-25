# 263. Ugly Number
Write a program to check whether a given number is an ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 6, 8 are ugly while 14 is not ugly since it includes another prime factor 7.

Note that 1 is typically treated as an ugly number.
## Solution1
``` js
/**
 * @param {number} num
 * @return {boolean}
 */
var isUgly = function(num) {
    //解法1：递归
    //Note that 1 is typically treated as an ugly number
    if(num===1){
        return true;
    }
    //less than or equals to 0, is also ugly number
    if(num<=0){
        return false;
    }
    
    if(num%2===0){
        return isUgly(num/2);
    }
    
    if(num%3===0){
        return isUgly(num/3);
    }
    
    if(num%5===0){
        return isUgly(num/5);
    }
    
    return false;
};
```

## Solution2
``` js
/**
 * @param {number} num
 * @return {boolean}
 */
var isUgly = function(num) {
    //解法2：循环
    //Note that 1 is typically treated as an ugly number
    if(num===1){
        return true;
    }
    //less than or equals to 0, is also ugly number
    if(num<=0){
        return false;
    }
    
    while(num%2===0){
        num=num>>1;
    }
    
    while(num%3===0){
       num=num/3;
    }
    
    while(num%5===0){
        num=num/5;
    }
    //if it equals to 1,that means ugly. Otherwise, not ugly
    return num===1;
    
};
```