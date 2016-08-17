# 165. Compare Version Numbers
Compare two version numbers version1 and version2.

If version1 > version2 return 1, if version1 < version2 return -1, otherwise return 0.

You may assume that the version strings are non-empty and contain only digits and the . character.

The . character does not represent a decimal point and is used to separate number sequences.

For instance, ``2.5`` is not "two and a half" or "half way to version three", it is the fifth second-level revision of the second first-level revision.

Here is an example of version numbers ordering:
```
0.1 < 1.1 < 1.2 < 13.37
```

## Solution1
``` js
/**
 * @param {string} version1
 * @param {string} version2
 * @return {number}
 */
var compareVersion = function(version1, version2) {
    var a=version1.split('.');
    var b=version2.split('.');

    var idx=0;
    var lena=a.length;
    var lenb=b.length;
    while(idx<lena && idx<lenb){
        var v1=parseInt(a[idx],10);
        var v2=parseInt(b[idx],10);
        // console.log("v1: "+v1,"v2: "+v2);
        if(v1===v2){
            idx++;
        }else if(v1<v2){
            return -1;
        }else{//v1>v2
            return 1;
        }
    }
    
    //for example: "01" "1"
    if(lena==lenb){
        return 0;
    }else if(lena<lenb){// "1" "1.X.X"
        while(parseInt(b[idx],10)===0){
           idx++;  
        }
        if(idx>lenb){//"1" "1.0.0"
            return 0;
        }
        return b[idx]>0?-1:0;
    }else{//"1.X.X" "1"
        while(parseInt(a[idx],10)===0){
           idx++;  
        }
        if(idx>lena){ //"1.0.0" "1"
            return 0;
        }
        return a[idx]>0?1:0;
    }
};
```
