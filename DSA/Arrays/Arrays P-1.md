## 2-Sum

Difficulty : Easy

I/P : `nums = [2,7,11,15], target = 9`

O/P : `[0,1]`

There are two ways approach this problem

1. Brute Force : Check each pair of 2 possible in the given array .
   Time Complexity : $O(n^2)$ , Space Complexity : $O(1)$
2. Optimized : Time Complexity : $O(n*log(n)$

Algo :

1. Create a map .
2. Iterate over the nums array .
3. Check if the target-nums present in the map or not .
4. if not present then store the element at the particular index in the map.
5. else push the elements into a vector if a match is found.

Code :

```cpp
unordered_map<int,int> mp;
        vector<int> ans;
        for(int i = 0 ; i<nums.size() ; i++){
                if(mp.find(target-nums[i])!=mp.end()){
                    ans.push_back(i);
                    ans.push_back(mp[target-nums[i]]);
                    break;
                }
                mp[nums[i]] = i;
        }
        return ans;
```

## 4-Sum

Difficulty : Medium.

I/P : `nums = [1,0,-1,0,-2,2], target = 0`

O/P : `[[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]`

Note : All the index’s must be different . $i=!j=!k=!l$

Brute Force :

1. Check for each quadruples in the array.
   Time Complexity : $O(n^4)$.

Better Approach :

1. Do a for loop for $ith$ and $jth$ and $Kth$ position .
2. Once we have allotted the positions of ith , jth and kth index then we just need to put all the element between jth and kth element in the hashSet , if they exist.
   Why ? Because if we consider the entire array elements then we may end up storing duplicate indices in out answer.
3. $nums[fourth] = target - (nums[ith]+nums[jth]+nums[kth]).$
4. Store $nums[kth]$ value in our hashset and check for the our fourth element in the hashset.

```cpp
set<vector<int>> st;
    for(int i = 0 ; i<nums.size() ; i++){
        for(int j = i+1 ; j<nums.size() ; j++){
                set<long long> hash_set;
            for(int k = j + 1 ; k<nums.size() ; k++){
                long long sum = nums[i]+nums[j];
                sum += nums[k];
                int l = target - sum;
                if(hash_set.find(l)!=hash_set.end()){
                    vector<int> temp{nums[i],nums[j],nums[k],l};
                    sort(temp.begin(),temp.end());
                    st.insert(temp);
                }
                hash_set.insert(nums[k]);
            }
        }
    }
    vector<vector<int>> ans(st.begin(),st.end());
    return ans;
}
```

Time Complexity : $O(n^3log(n))$ and Space Complexity : $O(n) + O(Q)$. where Q is the number of quadruples.

## Longest Consecutive Subsequence

Difficulty : Medium.

I/P : `nums = [100,4,200,1,3,2]`

O/P : `4`

Brute Force :

1. `for(i 0 to n ) :`
2. `counter = 1;`
3. `curr = nums[i]`
4. `while(binarysearch(nums[i]) {`
5. `curr = curr + 1.`
6. `counter++;`
7. `update ans.`

Time Complexity : $O(n^2)$ , Constant Space Complexity .

Better :

1. `sort(array)`
2. `longest = 0, curCol = 0 , lastSmal = min.`
3. `for ( 0 to n )`
   1. `counter = 0`
   2. `if ( arr[i] -1 == lastSmaller )`
      1. `counter + 1`
      2. `lastSmaller = arr[i]`
   3. `else if( arr[i] ≠ lastSmaller)`
      1. `counter + 1`
      2. `lastSmaller = arr[i]`
   4. `update longest .`
4. `return longest.`

Time Complexity : $O(nlogn+n )$

Optimal :

- Create a set data structure.
- declare a variable longest.
- Insert every element into the set.
- Traverse the set data structure
  if element -1 is not present in the set
  then initialize the counter to 1 .
  value variable to element.
  while variable + 1 is present in the set
  counter++
  update variable = variable +
- update the longest variable. \

```cpp
if(nums.size() == 0){
            return 0;
        }
       set<int> st;
       int longest=1;
       int counter = 0;
       for(int i = 0 ; i<nums.size() ; i++){
           st.insert(nums[i]);
       }


       for(auto it : st){
           if(st.find(it-1)==st.end()){
               counter = 1;
               int val = it;
               while(st.find(val+1)!=st.end()){
                   counter++;
                   val++;
               }
               longest = max(longest,counter);
           }
       }
       return longest;
```

Time Complexity : $O(n+n)$ . Considering set is taking log(n) to find elements.

## Largest Subarray with sum k

Subarray : Contiguous part of the array .

Brute Force :

1. Run for loop for the two pointers i and j
2. Run another for loop for calculating the sum between i and j positions
3. if sum == k then extract that subarray.

Time Complexity : $O(n^3)$ , Space Complexity : $O(1)$.

Better :

We can reduce the time complexity to $O(n^2)$ calculating the value of the sum when the j variable iterate.

More Better :

Hashing

1. We will hash the prefix sum value in a hash table .
2. When ever we encounter a value = prefix sum - target .
3. we will update the value of our answer .
4. make sure to prevent updating the hashed value in the hash map , Because if not done then this will ignore all the negative sum cases.

```cpp
unordered_map<int,int> mp;
        int ans = 0 ;
        int sum = 0;
        for(int i = 0 ; i<N ; i++){
            sum += A[i];
            if(sum == K){
                ans = max(ans , i+1);
            }
            int rem  = sum - K ;
            if(mp.find(rem) != mp.end()){
                ans = max(ans,i-mp[rem]);
            }
            if(mp.find(sum)==mp.end()){ // to prevent updaing the hashed value again and again we encounter sum
                mp[sum] = i;
            }
        }
        return ans;
```

Time Complexity : $O(n(log(n)+log(n))$. Space Complexity : $O(n).$ Note “The log(n) complexity may becomes O(n) in case of unordered map in c++”.

Optimal :

1. We take two pointers left and right.
2. Traverse till right pointer is less than n ( n is the number of elements in the array ).
3. The window of the ith and jth pointer moves to a size equivalent to the target.

```cpp
int left = 0;
        int right = 0;
        int sum = A[0];
        int ans = 0;
        while(right < N){
            while(sum > K && left <= right){
                sum -= A[left];
                left++;
            }
            if(sum == K){
                ans = max(ans,right-left+1);
            }
            right++;
            if(right < N) sum += A[right];
        }
        return ans;
```

Time Complexity : $O(2n).$ , Space Compexity : Constant.

## Count Subarrays with XOR sum equal to K

Difficulty : Medium.

Brute Force :

1. Generate all the subarrays and calculate the sum of each subarray and compare it with K.
2. if we found a match then increase the counter.

Time Complexity : $O(n^2)$ . Space Complexity : $O(1).$

Better :

1. Create a map and store a value with xor 0 and count 1 , for the case if we select empty subarray.
2. Traverse the array keep a xor_sum variable which will store the xor sum till now.
3. calculate the reminder using `rem = xor_sum ^ target` .
4. Increase the counter with the counter of the reminder present in the hasmap.
5. Increase the counter of the xor_sum in hashmap.

Intiution :

$$
XxorK =  xor \left( XR  \right)
$$

$$
 \left( XxorK  \right)  xorK =  xor \left( XK  \right)  xorK
$$

$$
X =  xor \left( XR  \right)  xor \left( K  \right)
$$

> Xor with K on both LHS and RHS.
> Final equation , We will search for number of time X occur in the HashMap.

Time Complexity : $O(n)$ in case of unorderd hashmap . or $O(n.log(n))$ in the case of normal hashmap.

Space Complexity : $O(n).$ Because their can be a case where we store all the unique characters of the array into out hashmap.

## Longest Substring without Repeating Characters

I/P : **`abcabcbb`**

O/P : `3`

Brute Force :

To generate all the sub-strings and check the weather it contains unique characters or not.

and store the maximum length among them .

Time Complexity : $O(n^2).$ Space Complexity : $O(n).$

Better :

1. Create two pointers left and right initialized to 0.
2. Declare a set .
3. Move the right pointer to the left and push the element to the set as we encounter them till a duplicate value is found.
4. Now we need to move the left pointer towards the right pointer until left ≤ right and the duplicate element from the set is removed ( make sure to remove the element form the set as we move our left pointer ).

Time Complexity : $O(2n).$ In the worst case the right and left may traverse the entire array twice . Space Complexity : $O(n).$ for the set data structure.

Optimal :

1. Create a character map to store all the last index values of the characters in the string.
2. Take two pointers left , right .
3. Traverse till right < n .
4. Update left to the required recent index.
5. Calculate the length of the substring.
6. Update the map value for each occurrence with right pointer.

```cpp
vector<int> mpp(256,-1);
    int right= 0, left = 0 , maxlen = 0 , n = s.size();
    while(right < n){
        if(mpp[s[right]]!=-1){
            left = max(left,mpp[s[right]]+1);
        }
        maxlen = max(maxlen,right-left+1);
        mpp[s[right]] = right;
        right++;
    }
    return maxlen;
```

Time Complexity : $O(n).$ only . Space Complexity : $O(n).$

## Pascal’s Triangle

I/P : `numRows = 5`

O/P : `[[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]`

Variations

1. Find the element at specific row and column.

   Combination formula :
   If n = row - 1 , r = col -1 then this will give element present.

   $$
    \dfrac{  n  !    }{  r  !    \left( n-r  \right)    !    }
   $$

2. The element in a specific row.

```cpp
vector<int> genRow(int rowNum){
        vector<int> temp;
        temp.push_back(1);
        long long ans = 1;
        for(int i = 1 ; i<rowNum ; i++){
            ans *= (rowNum - i);
            ans /= (i);
            temp.push_back(ans);
        }
        return temp;
    }
```

Time complexity : $O(rowNum)$, Space complexity : $O(1).$

1. Find the entire Pascal’s triangle.

```cpp
vector<vector<int>> generate(int numRows) {
        vector<vector<int>> ans;
        for(int i = 1 ; i<=numRows ; i++){
            ans.push_back(genRow(i));
        }
        return ans;
    }
```

Time complexity : $O(n^2)$, Space complexity : $O(1).$

## Next permutation

I/P : `[1,3,2]`

O/P : `2 , 1 , 3`

> The total number of permutations of a given array n! , where n is the length of the given array.

Approach :

1. Brute :

   Generate all the permutations of the given array using recursion,
   then put them into some storage and search for the next permutation in that.

   Time complexity : $O(n!*n)$ , where n! is for generating all the permutations and n is for iterating each permutation .

2. In C++ STL there exist a inbuilt function called `next_permutation(begin,end);` which will generate next permutation 😆.
   Time complexity : $O(n/2)$, where n is no of swaps.
3.
