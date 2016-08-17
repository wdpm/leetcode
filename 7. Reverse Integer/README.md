# 7. Reverse Integer
Reverse digits of an integer.
```
Example1: x = 123, return 321
Example2: x = -123, return -321
```

## Have you thought about this?
- Here are some good questions to ask before coding. Bonus points for you if you have already thought through this!

- If the integer's last digit is 0, what should the output be? ie, cases such as 10, 100.

- Did you notice that the reversed integer might overflow? Assume the input is a 32-bit integer, then the reverse of 1000000003 overflows. How should you handle such cases?

- For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

## Solution1
``` js
/**
 * @param {number} x
 * @return {number}
 */
var reverse = function(x) {
    if(x===0) return x;
    if(x>0){
        var str=x.toString().split('').reverse().join('');
        var res=parseInt(str,10);
        // console.log(res);
        return res>Math.pow(2,31)?0:res;
    }
    
    if(x<0){
        var str2=x.toString();
        //remove "-" sign symbol
        str2=str2.substr(1,str2.length);
        str2=str2.split('').reverse().join('');
        var res2=parseInt(str2,10);
        // console.log(res2);
        return res2>Math.pow(2,31)?0:(-1)*res2;
    }
};
```