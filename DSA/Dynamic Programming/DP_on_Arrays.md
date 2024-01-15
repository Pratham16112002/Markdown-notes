# Dynamic Programming

"Do not repeat the past".

## Buy and Sell stock 1

Input: `[7,1,5,3,6,4]`  
Output : `5`

> Note before selling a stock you need to buy one stock first.

In general you need to find a particular pair with maximum difference between them and first element should be less than the other element.

Brute force :

- Running two nested for loops are look for the particular pairs.

Time complexity : $O(n^2)$

Optimal approach :

- Using dynamic programming and storing the minimum element from the array.
- Check the compatibility with the current element and the minimum element.

Code :

```cpp
int maxProfit(vector<int>& prices) {
        int mini = prices[0] , profit = 0 , cost = 0;
        for(int i = 1 ; i<prices.size() ; i++){
            cost = prices[i] - mini;
            profit = max(profit,cost);
            mini = min(mini,prices[i]);
        }
        return profit;
    }
```

Time complexity : $O(n)$ , Space complexity is constant.
