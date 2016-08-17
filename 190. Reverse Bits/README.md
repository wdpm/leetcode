# 190. Reverse Bits
Reverse bits of a given 32 bits unsigned integer.

For example, given input 43261596 (represented in binary as **00000010100101000001111010011100**), 
return 964176192 (represented in binary as **00111001011110000010100101000000**).

**Follow up**:

If this function is called many times, how would you optimize it?
## Solution1
``` js
/**
 * @param {number} n - a positive integer
 * @return {number} - a positive integer
 */
var reverseBits = function(n) {
    var bits=n.toString(2).split('');
    var prefixZeros="";
    for(var i=bits.length;i<32;i++){
        prefixZeros+=0;
    }
    bits.unshift(prefixZeros);
    var reverseBits=bits.reverse().join('');
    var num2=parseInt(reverseBits,2);
    return num2;
};
```