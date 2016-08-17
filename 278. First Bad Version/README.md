# 278. First Bad Version
You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of 
your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.

Suppose you have ``n`` versions ``[1, 2, ..., n]`` and you want to find out the first bad one, which causes all the following ones to be bad.

You are given an API ``bool isBadVersion(version)`` which will return whether version is bad. Implement a function to 
find the first bad version. You should minimize the number of calls to the API.

## Solution1
``` js
/**
 * Definition for isBadVersion()
 * 
 * @param {integer} version number
 * @return {boolean} whether the version is bad
 * isBadVersion = function(version) {
 *     ...
 * };
 */

/**
 * @param {function} isBadVersion()
 * @return {function}
 */
var solution = function(isBadVersion) {
    /**
     * @param {integer} n Total versions
     * @return {integer} The first bad version
     */
    return function(n) {
        var l=1;
        var r=n;
        while(l<=r){
            var mid=parseInt((l+r)/2,10);
            
            if(!isBadVersion(mid-1) && isBadVersion(mid) && isBadVersion(mid+1)){
                return mid;
            }else if(isBadVersion(mid)){//on the left part
                r=mid-1;
            }else{//on the right part
                l=mid+1;
            }
        }
        
        return l;
    };
};
```
