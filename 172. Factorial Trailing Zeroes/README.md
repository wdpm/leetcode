# 172. Factorial Trailing Zeroes
Given an integer n, return the number of trailing zeroes in n!.

**Note**: Your solution should be in logarithmic time complexity.
## Solution1
``` js
/**
 * @param {number} n
 * @return {number}
 */
var trailingZeroes = function(n) {
    
     //let n! = k*10^M = k*(2*5)^M
     //we should caculate M
     //because n!=n*(n-1)*(n-2)*...*3*2*1, then we should caculate which contains 5 as factorial,finally add them as result
     //for example:25!=...*5*...*10*...*15*...*20*...*25,
     //5 10 15 20 contribute 1 time; but 25 contributes 2 time,because 25=5*5.
     var count=0;
     while(n){
         count+=parseInt(n/5);
         n=parseInt(n/5);
     }
     return count;
};
```