# Array 3

## Rearrange the elements of the array by sign

I/P : `[3,1,-2,-5,2,-4]`  
O/P : `[3,-2,1,-5,2,-4]`

You will be given and array which contains +ve and -ve integers and you have to rearrange the elements in such a way that adjacent elements have opposite signs.

**Brute force**:

- Take two arrays positive and negative.
- Store the respective elements in the respective arrays.
- Now, put all the elements in the positive array on the even indices including 0.
- Put all the negative elements on the odd indices.

Time complexity : $O(n) + O(n)$, Space complexity : $O(n)$.

**Optimal**:

- Take two pointers, one denotes the position of positive elements from 0 and the other denotes the position of the negative index from 1.
- If the current element is positive we add it to the answer and move the positive index by 2 position, If the current element is negative we add it the answer and move the negative index by 2.

```cpp
vector<int> rearrangeArray(vector<int>& nums) {
        int pos = 0 , neg = 1;
        vector<int> ans(nums.size());
        for(int i = 0 ; i<nums.size() ; i++) {
            if(nums[i] > 0 ){
                ans[pos] = nums[i];
                pos = pos+2;
            }
            else {
                ans[neg] = nums[i];
                neg = neg + 2;
            }
        }
        return ans;
    }
```

> The time complexity is reduced to $O(n)$ from $O(2n)$.

## Longest Consecutive subsequence

I/P : `[1,9,3,10,4,20,2]`  
O/P : `4`

Brute force :

- Run a for loop for the given array.
- For each element check if the next element is present in the array or not.
- If present then find the consecutive next element in the array and increment the count.
- At the end, return the maximum count.

Time complexity : $O(n^2)$ , Space cpomplexity : $O(1)$.

Better approach :

- Sort the array.
- Count the number of consecutive elements in the array.
- After sorting, there is no need to check for the previous elements in the array which is a great improvement in time complexity.

Approach :

```cpp
 int longestConsecutive(vector<int>& nums) {
        if(nums.size() == 0) return 0;
        int longest = 1 , curr_cnt , left_smaller = INT_MIN ;
        sort(nums.begin(),nums.end());
        for(int i = 0 ; i<nums.size() ; i++){
            if(left_smaller == nums[i]-1){
                left_smaller = nums[i];
               curr_cnt++;
            }
            else if(left_smaller != nums[i]){
                left_smaller = nums[i];
                curr_cnt = 1;
            }
            longest = max(longest,curr_cnt);
        }
        return longest;

    }
```

Time complexity : $O(nlogn + n)$ , Space complexity : $O(1)$.

Optimal approach :

- We will be using the unordered set to store the elements of the array.
- Now, we will iterate over the set and check if the previous element is present or not.
  - If it is not present then we will start our brute force count logic.
  - If it is present then we will simply skip that element.

```cpp
int longestConsecutive(vector<int>& nums) {
        if(nums.size() == 0) return 0;
        unordered_set<int> st;
        for(int it : nums){
            st.insert(it);
        }
        int longest = 1;
        for(auto it : st){
            if(st.find(it-1) == st.end()){
                int cnt = 1;
                int x = it;
                while(st.find(x+1) != st.end()){
                    cnt++;
                    x = x +1;
                }
                longest = max(longest , cnt);
            }
        }
        return longest;
    }
```

Time complexity : $O(n)$ , Space complexity : $O(n)$.
