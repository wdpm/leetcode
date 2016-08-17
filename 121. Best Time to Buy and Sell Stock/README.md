# 121. Best Time to Buy and Sell Stock
Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.

Example 1:
```
Input: [7, 1, 5, 3, 6, 4]
Output: 5

max. difference = 6-1 = 5 (not 7-1 = 6, as selling price needs to be larger than buying price)
```
Example 2:
```
Input: [7, 6, 4, 3, 1]
Output: 0

In this case, no transaction is done, i.e. max profit = 0.
```
## Solution1
``` js
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function(prices) {
    var maxDiff=0;
    var minPrice=Number.MAX_VALUE;
    for (var i=0,len=prices.length;i<len;i++){
        //求得当前最小价格
        minPrice=Math.min(minPrice,prices[i]);
        //将(当前价格-当前最小价格)，与当前最大差值比较
        maxDiff=Math.max(maxDiff,prices[i]-minPrice);
    }
    
    return maxDiff;
};
```