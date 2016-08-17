# 299. Bulls and Cows
You are playing the following Bulls and Cows game with your friend: You write down a number and ask your friend to guess 
what the number is. Each time your friend makes a guess, you provide a hint that indicates how many digits in said guess 
match your secret number exactly in both digit and position (called "bulls") and how many digits match the secret number
but locate in the wrong position (called "cows"). Your friend will use successive guesses and hints to eventually derive the secret number.
 
For example:
```
Secret number:  "1807"
Friend's guess: "7810"
```
Hint: ``1`` bull and ``3`` cows. (The bull is ``8``, the cows are ``0``, ``1`` and ``7``.)

Write a function to return a hint according to the secret number and friend's guess, use ``A`` to indicate the bulls 
and ``B`` to indicate the cows. In the above example, your function should return ``"1A3B"``.

Please note that both secret number and friend's guess may contain duplicate digits, for example:
```
Secret number:  "1123"
Friend's guess: "0111"
```
In this case, the 1st ``1`` in friend's guess is a bull, the 2nd or 3rd ``1`` is a cow, and your function should return ``"1A1B"``.
You may assume that the secret number and your friend's guess only contain digits, and their lengths are always equal.
## Solution1
``` js
/**
 * @param {string} secret
 * @param {string} guess
 * @return {string}
 */
var getHint = function(secret, guess) {
    //精确匹配,很容易算出
    var countA=0;
    //countB是个难点，使用全匹配减去精确匹配可以获得countB，即异位匹配
    var countTotal=0;
    var len=secret.length;
    for(var i=0;i<len;i++){
        if(secret[i]===guess[i]){
            countA++;
        }
    }
    //数字计数器，记录secret的数字次数
    var map=new Array(10).fill(0);
    for(var j=0;j<len;j++){
        map[secret[j]]++;
    }
    // console.log(map);
    //遍历guess，相应减去secret的数字次数，如果大于1代表：匹配(可能是对位匹配，也可能是异位匹配)，我称之为全匹配
    for(var k=0;k<len;k++){
        if(--map[guess[k]]>=0){
            countTotal++;
        }
    }
    return countA+'A'+(countTotal-countA)+'B';
};
```
