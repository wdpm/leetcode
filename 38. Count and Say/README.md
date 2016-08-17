# 38. Count and Say
The count-and-say sequence is the sequence of integers beginning as follows:

``1, 11, 21, 1211, 111221, ...``
- `1` is read off as `"one 1"` or `11`.
- `11` is read off as `"two 1s"` or `21`.
- `21` is read off as `"one 2, then one 1"` or `1211`.

Given an integer n, generate the nth sequence.

Note: The sequence of integers will be represented as a string.
## Solution1
``` js
/**
 * @param {number} n
 * @return {string}
 */
var countAndSay = function(n) {
    //direct solution
    if(n===1){
        return 1+"";
    }else{
        var a=[];
        a[1]=[1];
        a[2]=[1,1];
        
        //caculate i=3,4,...,util n
        for(var i=3;i<=n;i++){
            //init a[i]
            a[i]=[];
            // console.log("a["+(i-1)+"]: "+a[i-1]);
            
            //mark repeat times of a digit
             var repeat=1;
             
            for(var j=0,len=a[i-1].length;j<len;j++){
                
                if(j!==len-1){
                    if(a[i-1][j]===a[i-1][j+1]){
                        // console.log("enter #1");
                        repeat++;
                        //if a[j+1] is not the last element in a[i-1],go to next lopp.Otherwise,skip ``continue``
                        // if(j+1!==a[i-1].length-1){
                           continue; 
                        // }
                    }else{
                        // console.log('enter #2');
                        //not equal to previous digit
                        a[i].push(repeat);
                        a[i].push(a[i-1][j]);
                        // console.log("before reset, repeat: "+repeat);
                        //reset repeat
                        repeat=1;

                        // console.log("in #2: "+a[i]);
                        continue;
                    }
                }
                
                // console.log('enter #3');
                //not equal to previous digit
                a[i].push(repeat);
                a[i].push(a[i-1][j]);
                //reset repeat
                repeat=1;
            }
            // console.log("======================");
        }
       
        return a[n].join('');
    }    
};
```