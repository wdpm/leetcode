# 66. Plus One
Given a non-negative number represented as an array of digits, plus one to the number.

The digits are stored such that the most significant digit is at the head of the list.
``` java
public class Solution {
    public int[] plusOne(int[] digits) {
       int len=digits.length;
       for(int i=len-1;i>=0;i--){
           //当前位置小于9，加1，返回
           if(digits[i]<9){
               digits[i]++;
               return digits;
           }
           //当前位置为9，置为0
           digits[i]=0;
       }
       
       //代码运行到这里，代表是该数组数字全为9，需要进位，添加前置1
       int[] newDigits=new int[len+1];
       newDigits[0]=1;
       return newDigits;
    }
}
```
