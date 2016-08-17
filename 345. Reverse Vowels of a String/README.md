# 345. Reverse Vowels of a String
Write a function that takes a string as input and reverse only the vowels of a string.

**Example 1**:
Given s = "hello", return "holle".

**Example 2**:
Given s = "leetcode", return "leotcede".

**Note**:
The vowels does not include the letter "y".
## Solution1
``` js
/**
 * @param {string} s
 * @return {string}
 */
var reverseVowels = function(s) {
    //vowels array
    if(s.length<=1){
        return s;
    }
    var vowels=['a','e','i','o','u','A','E','I','O','U'];

    var i=0;
    var j=s.length-1;
    var s=s.split('');
    while(i<=j){
        //ignore non-vowels 
        while(vowels.indexOf(s[i])===-1&&i<=j){
            i++;
        }
        
        while(vowels.indexOf(s[j])===-1&&i<=j){
            j--;
        } 
        
        if(i<=j){
            swap(s,i,j);
            i++;
            j--;
        }
    }
    
    return s.join('');
    
    function swap(s,i,j){
        var tmp=s[i];
        s[i]=s[j];
        s[j]=tmp;
    }
};
```