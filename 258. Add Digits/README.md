# 258. Add Digits
Given a non-negative integer num, repeatedly add all its digits until the result has only one digit.

For example:

Given num = 38, the process is like: 3 + 8 = 11, 1 + 1 = 2. Since 2 has only one digit, return it.

Follow up:
Could you do it without any loop/recursion in O(1) runtime?
``` java
public class Solution {
    public int addDigits(int num) {
      //解法1：
      while(num>=10){
       //分离每个位上的数字，将其相加
       //例38，3+8=11，1+1=2；
       //例112，11+2=13，1+3=4；
       num=(num/10)+(num%10);
      }
      return num;
      
      //解法2：
      //https://en.wikipedia.org/wiki/Digital_root  #Significance and formula of the digital root
      //https://en.wikipedia.org/wiki/Floor_and_ceiling_functions
      //return num-9*((num-1)/9);
      
    }
}
```
