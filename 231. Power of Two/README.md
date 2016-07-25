# 231. Power of Two
Given an integer, write a function to determine if it is a power of two.
``` java
public class Solution {
    public boolean isPowerOfTwo(int n) {
        //小于等于0,不是2的次方，直接返回false
        if(n<=0){
            return false;
        }
        
        //为奇数且不为1，不是2的次方，直接返回false
        if(n%2!=0 && n!=1){
            return false;
        }
        
        //为偶数,不断除以2
        while(n%2==0){
            n=n/2;
        }
        
        //为1，代表是2的次方
        if(n==1){
          return true;  
        }else{//不为1， 代表不是2的次方
          return false;
        }

    }
}
```