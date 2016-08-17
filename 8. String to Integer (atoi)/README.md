# 8. String to Integer (atoi)
Implement atoi to convert a string to an integer.

**Hint**: Carefully consider all possible input cases. If you want a challenge, please do not see below and ask yourself what are the possible input cases.

**Notes**: It is intended for this problem to be specified vaguely (ie, no given input specs). You are responsible to gather all the input requirements up front.

**Requirements for atoi**:

The function first discards as many whitespace characters as necessary until the first non-whitespace character is found. Then, starting from this character, takes an optional initial plus or minus sign followed by as many numerical digits as possible, and interprets them as a numerical value.

The string can contain additional characters after those that form the integral number, which are ignored and have no effect on the behavior of this function.

If the first sequence of non-whitespace characters in str is not a valid integral number, or if no such sequence exists because either str is empty or it contains only whitespace characters, no conversion is performed.

If no valid conversion could be performed, a zero value is returned. If the correct value is out of the range of representable values, INT_MAX (2147483647) or INT_MIN (-2147483648) is returned.

## Solution1
``` js
/**
 * @param {string} str
 * @return {number}
 */
var myAtoi = function(str) {
    //preprocess:
    //discards whitespace characters
    var a=str.trim().split(' ');
    // console.log(a);
    //1. If the first sequence of non-whitespace characters in str is not a valid integral number, 
    //or if no such sequence exists because either str is empty or it contains only whitespace characters, no conversion is performed.
    
    //2. takes an optional initial plus or minus sign followed by as many numerical digits as possible, 
    //and interprets them as a numerical value.
    var digits='0123456789';
    if(a[0].length===0){
        return 0;
    }else if(a[0].length===1){
        if(digits.indexOf(a[0][0])===-1){
            return 0;
        }else{
            return +a[0][0];
        }
    }else{
        //a[0].length>=2
        var sign="";
        if(a[0][0]==="+"||a[0][0]==="-"){
            sign=a[0][0];
            a[0]=a[0].substr(1,a[0].length);
        }
        // console.log(a[0]);
        //format is valid,but the string can contain additional characters after those that form the integral number, 
        //which are ignored and have no effect on the behavior of this function.
        var ret="";
        for(var i=0,len=a[0].length;i<len;i++){
            if(digits.indexOf(a[0][i])!==-1){
                ret+=a[0][i];
            }else{
                break;
            }
        }

        // console.log(ret);
        //convert string to number
        var sum=0;
        var len2=ret.length;
        for(var j=len2-1;j>=0;j--){
            sum+=ret[j]*Math.pow(10,len2-j-1);
        }
        sum=sign?(Number)(sign+sum):sum;
        return Math.max(Math.min(sum,Math.pow(2,31)-1),-1*Math.pow(2,31));
    }
};
```
