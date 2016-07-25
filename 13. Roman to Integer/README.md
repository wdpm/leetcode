# 13. Roman to Integer
Given a roman numeral, convert it to an integer.

Input is guaranteed to be within the range from 1 to 3999.
``` java
public class Solution {
    public int romanToInt(String s) {
        //参考链接:https://discuss.leetcode.com/topic/49331/my-accepted-simple-java-solution-with-switch-case-so-easy
        // pre means previous Roman character, cur means current character
        int pre = 0, cur = 0, result = 0; 
        //遍历每个字符
        for(int i=0; i< s.length(); i++){
            //每个字符串转化为十进制数
            switch(s.charAt(i)){
                case 'M': cur = 1000;
                    break;
                case 'D': cur = 500;
                    break;
                case 'C': cur = 100;
                    break;
                case 'L': cur = 50;
                    break;
                case 'X': cur = 10;
                    break;
                case 'V': cur = 5;
                    break;
                case 'I': cur = 1;
                    break;
            }
            //如果右边cur比左边pre大，需要加上(cur-pre)；此外，(result-pre)表示抵消之前加上左边的结果
            if(cur > pre ){
                result = (result-pre) + (cur-pre);
            }else{//如果右边cur比左边pre小，直接加上即可 
                result += cur ; 
            }
            //将当前cur变为pre，继续迭代
            pre = cur ;
        }
        return result;
    }
}
```