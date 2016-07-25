#344. Reverse String
Write a function that takes a string as input and returns the string reversed.

Example:
Given s = "hello", return "olleh".
``` js
/**
 * @param {string} s
 * @return {string}
 */
var reverseString = function(s) {
    var tempStr="";
    for(var i=s.length-1;i>=0;i--){
        tempStr+=s.charAt(i);
    }
    return tempStr;
};
```