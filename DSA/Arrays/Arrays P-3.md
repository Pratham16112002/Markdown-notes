## Minimum array length required to after pair removal

<span style='color:lightgreen;'> Very good question</span>

Input : `nums = [1,3,4,9]`

Output : `0`

[Link to the problem 🍻 ](https://leetcode.com/problems/minimum-array-length-after-pair-removals/)

Approach :

1. We need to create a map to count the frequency of each element in the array and then store it in a HashMap.
2. Get the element with the maximum frequency.
3. Compare the maximum frequency with n/2

   Because if it is less than the n/2 then it will get cancelled by other half of the array, In the other case where it is greater than n/2 then the remaining elements is equal to maxi - ( n - maxi ) .

   Note in the less than case if the array length is even then all the duplicates of that element will get cancelled where as if array length is odd then there will always exist one element which will not get cancelled so we return 1.

```cpp
public:
    int minLengthAfterRemovals(vector<int>& nums) {
        unordered_map<int,int> mp;
        int n = nums.size();
        for(int i = 0 ; i<nums.size() ; i++){
            mp[nums[i]]++;
        }
        int maxi_ele = -1e9;
        for(auto it : mp){
            maxi_ele  = max(maxi_ele,it.second);
        }
        if(maxi_ele <= n/2){
            if(n%2 == 0){
                return 0;
            }
            else {
                return 1;
            }
        }
        return 2*maxi_ele - n;
    }
};
```

## Beautiful Tower

You will be given an array of maximum possible heights , where each element represents the maximum height possible.
<span style='color:blue;'>Very Intuitive Question</span>
You need to make that a tower height that is beautiful

1. `1<= height[i] <= maxHeight[i]`
2. height should be mountain.
   **Mountain**
3. For all `0 < j <= i`, `heights[j - 1] <= heights[j]`
4. For all `i <= k < n - 1`, `heights[k + 1] <= heights[k]`
   Brute Approach :
   For every possible element we will try to make mountain and check for the maximum sum tower.

```cpp
int makeMount(int index, std::vector<int> &num) {
  int n = num.size();
  long long total_sum = num[index];
  // For left part
  int nextHeight = num[index];
  for (int i = index - 1; i >= 0; i--) {
    int curr = 0;
    if (num[i] > nextHeight) {
      curr = nextHeight;
    } else {
      curr = num[i];
    }
    nextHeight = curr;
    total_sum += curr;
  }
  int prevHeight = num[index];
  for (int i = index + 1; i < n; i++) {
    int curr = 0;
    if (num[i] > prevHeight) {
      curr = prevHeight;
    } else {
      curr = num[i];
    }
    prevHeight = curr;
    total_sum += curr;
  }
  return total_sum;
}
```

This logic will run for each index of the array.
Time complexity : $O(n^2)$ , Space complexity : $O(1)$.

## Minimum Operations to make array empty

<span style='color:red;'>Very easy question but intuitive</span><br>
**Input** `nums = [2,3,3,2,2,4,2,3,4]`<br>
**Output** `4`<br>

> If not able to make the array empty then return -1 <br>

As we need to return the minimum operations then we must start dviding the number by 3 First. <br>

$$count =  ceil \left(  \dfrac{ count  }{ 3 \cdot   \left( 1.0  \right)    }    \right)   $$

This is the formula we will be using for this question. <br>

The only condition where we will not able to make operation is 1.<br>

```cpp
class Solution {
public:
    int minOperations(vector<int>& nums) {
        unordered_map<int,int> mp;
        for(int i = 0 ; i<nums.size() ; i++){
            mp[nums[i]]++;
        }
        int minimum_operations = 0;
        for(auto it : mp){
            if(it.second == 1){
                return -1;
            }
            minimum_operations += ceil(it.second/(3*(1.0)));
        }
        return minimum_operations;
    }
};
```

Time complexity : $O(n)$ , Space Complexity : $O(m)$ , where m is the number of unique element present in the given array.<br>

### Minimum sum of mountain triplet

<span style='color:Tomato'>Medium Level Question</span>

You will be given **0-Indexed** array.<br>
Need to find a triplet which satisfies the condition for (i, j, k): <br>

1. $i<j<k$
2. $nums[i]<nums[j]$ and $nums[j]>nums[k]$

**Approach**:<br>
Calculate the left_min_prefix and right_min_prefix of the given array.<br>

**Code**: <br>

```cpp
int solve(vector<int> &nums){
  int curr_idx = 1;
  int n = nums.size();
  vector<int> left_min(n);
  left_min[0] = nums[0];
  for(int i = 1 ; i<n ; i++){
   left_min[i] = min(left_min[i-1],nums[i]);
  }
  vector<int> right_min(n);
  right_min[n-1] = nums[n-1];
  for(int i = n -2 ; i>=0 ; i--){
    right_min[i] = min(right_min[i+1],nums[i]);
  }
  int mini = 1e9;
 for(int i = 1 ; i<n-1 ; i++){
    if(nums[i] > left_min[i-1] && nums[i] > right_min[i+1]){
      mini = min(mini,nums[i] + left_min[i-1] + right_min[i+1]);
    }
 }
 return mini;
}
```

Time complexity : $O(n+n+n)$, Space complexity : $O(2n).<br>

Taking too much space... 😵‍💫
