# 67. Add Binary
Given two binary strings, return their sum (also a binary string).

For example,
```
a = "11"
b = "1"
Return "100".
```
## Solution1
``` js
/**
 * @param {string} a
 * @param {string} b
 * @return {string}
 */
var addBinary = function(a, b) {
    var lena=a.length;
    var lenb=b.length;
    
    var i=0;
    var carry =0;
    var res="";
    while(i<lena||i<lenb||carry!==0){
        var ai=(i<lena)?+a[lena-1-i]:0;
        var bi=(i<lenb)?+b[lenb-1-i]:0;
        //(ai+bi+carry)%2 is the sum of current position
        res=(ai+bi+carry)%2+res;
        // console.log(res);
        //get carry for next higher position
        carry=parseInt((ai+bi+carry)/2);
        i++;
    }
    
    return res;
    
};
```