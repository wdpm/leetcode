# 191. Number of 1 Bits
Write a function that takes an unsigned integer and returns the number of ’1' bits it has (also known as the Hamming weight).

For example, the 32-bit integer ’11' has binary representation 00000000000000000000000000001011, so the function should return 3.
``` js
/**
 * @param {number} n - a positive integer
 * @return {number}
 */
var hammingWeight = function(n) {
     var oneCount=0;
     //终止条件是n==0
     while(n){
         //reminder is 1
         if(n%2==1){
             oneCount++;
         }
         //必须转换为int类型
         n=parseInt(n/2);

     }
     
     return oneCount;
};
```
