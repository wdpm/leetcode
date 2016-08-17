# 6. ZigZag Conversion
The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)
```
P       A       H       N
  A   P   L   S   I   I   G
    Y       I       R
```
And then read line by line: ```"PAHNAPLSIIGYIR"```
Write the code that will take a string and make this conversion given a number of rows:
``` js
string convert(string text, int nRows);
```
convert(```"PAYPALISHIRING"```, 3) should return ```"PAHNAPLSIIGYIR"```
## Solution1
``` js
/**
 * @param {string} s
 * @param {number} numRows
 * @return {string}
 */
var convert = function(s, numRows) {
    //reference: https://segmentfault.com/a/1190000005751185
    
    //0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16          s.length()=17
    //P A Y P A L I S H I R  I  G  I  N  G  H
    
    //P               H                     H
    //  A           S   I                G
    //    Y       I       R           N
    //      P   L            I     I
    //        A                 G
    //
    
    //show index
    //0               8                     16      i=0, initialDistance=8, magic=8,
    //  1           7   9                15         i=1, initialDistance=6, magic=8,
    //    2       6      10          14             i=2, initialDistance=4, magic=8,
    //      3   5           11    13                i=3, initialDistance=2, magic=8,
    //        4                12                   i=4, initialDistance=0(later set to 8), magic=8,
    //
    if(numRows===1){
        return s;
    }
    
    var magic=2*numRows-2;
    var initialDistance=magic;
    var ret="";
    for(var i=0;i<numRows;i++){
        ret+=addOneLine(i,initialDistance,magic,s);
        //
        initialDistance=initialDistance-2;
    }
    
    return ret;
    
    //helper function
    function addOneLine(start,stepLength,magic,s){
        var result="";
        while(start<s.length){
            if(stepLength===0){
                stepLength=magic;
            }
            result+=s[start];//append to result
            start+=stepLength;//caculate next ``start`` index
            stepLength=magic-stepLength;//caculate next ``stepLength``
        }
        return result;
    }
};
```