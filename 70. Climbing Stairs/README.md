# 70. Climbing Stairs
You are climbing a stair case. It takes n steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?
## Solution1
``` js
/**
 * @param {number} n
 * @return {number}
 */
var climbStairs = function(n) {

     //fibonacci array
     var a=[];
     //no use a[0]
     a[0]=0;
     a[1]=1;
     a[2]=2;
     
     if(n<3){
         return a[n];
     }
     if(n>=3){
         for(var i=3;i<=n;i++){
             a[i]=a[i-1]+a[i-2];
         }
     }
     return a[n];
     
};
```