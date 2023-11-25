## Reverse Pairs

You will be given an array .

Difficulty : hard.

Output the number of all the pairs that exist within the array and satisfy :

$nums[i] > nums[j]*2$. where $i < j .$

Brute Force :

1. Check for each index pair present in the array .
2. Count those pairs and return it.

Time Complexity : $O(n^2).$ Space complexity : constant.

Optimal Approach :

1. We will be using merge Sort approach to solve this solution .
2. The Trick in this question is that when are we merging the two part of the array.

   1. We maintain a counter i and j ,
   2. ith pointer will traverse the first sorted part , jth pointer will traverse the second sorted part .
   3. move the jth pointer untill the condition is not satisfied.
   4. Then calculate the count using the formula ;

   Formula : $cnt +=(j-(mid+1));$

Code :

```cpp
int merge(vector<int>& nums , int low , int mid , int high){
        int j = mid + 1;
        int cnt=0;
        for(int i = low ; i<= mid ; i++){
            while(j<=high && nums[i] > 2LL * nums[j]){
                j++;
            }
            cnt +=(j-(mid+1));
        }
        vector<int> temp;
        int left = low , right = mid+1;
        while(left <=mid && right <= high){
            if(nums[left] > nums[right]){
                temp.push_back(nums[right++]);
            }
            else {
                temp.push_back(nums[left++]);
            }
        }
        while(left<=mid){
            temp.push_back(nums[left++]);
        }
        while(right<=high){
            temp.push_back(nums[right++]);
        }
        for(int i = low ; i<=high ; i++){
            nums[i] = temp[i-low];
        }
        return cnt;
    }
    int mergeSort(vector<int>& nums,int low , int high){
        if(low >= high){
            return 0;
        }
        int mid = (low + high)/2;
        int inv = mergeSort(nums,low,mid);
        inv += mergeSort(nums,mid+1,high);
        inv += merge(nums,low,mid,high);
        return inv;
    }
return mergeSort(nums,0,nums.size() - 1);
```

Time Complexity : $O(nlog(n) + n + n)$ . Space Complexity : $O(n).$ for the temporary array that we are using.

## Grid Unique Paths

A grid will be given you need to find a path from the (0,0) index to bottom-right most cell of the grid.

Brute Force :

1. Using simple recursion to traverse each possible path from the source to the destination.
2. Note only two possible path are possible from any cell which are bottom and right .
3. Base case would be if i exceeds the row size and j exceeds the column size.
4. return the addition for the left and right call .

```cpp
int help(int i , int j , int m , int n){
        if(i == m -1 && j == n-1 ){
            return 1;
        }
        if(i >=m || j >=n ) return 0;
        return help(i+1,j,m,n) + help(i,j+1,m,n);
    }
```

Both the Time and Space complexity are exponential in nature , because we are trying out all possible paths.

We can reduce the Time complexity by memorization technique to $O(n*m).$ and space complexity to $O(n*m).$ for storing the solutions.

## Search in 2D Matrix

I/P : Target = 3
![](https://i.imgur.com/ctqqupF.png)
O/P : true.

Brute Force :

1. We will do binary search for target on each row of the matrix .
2. if element is found we return true , else return false.

Time Complexity : $O(nlog(m)).$ where n is the no of rows and m is the no of columns .

Better :

1. Place the pointers on the top-right element of the matrix.
2. if the current cell has a value less then target then move the pointers to the left cell.
3. else if current cell has a value greater than target then move the pointers to the bottom cell.
4. once the target is found we return the value / true .

We are taking advantage of the sorted behavior of the given grid.

We stop the traversal once we reach outside of the grid , which means that target is never found in the grid.

Optimal :

1. We will perform binary search on the entire grid .
2. low = 0 and high = n \* m - 1 .
3. Find row = mid/column and column = mid % column with mid.

```cpp
if(matrix.size() == 0){
            return false;
        }
        int m = matrix.size();
        int n = matrix[0].size();
        int low = 0, high = (m*n)-1;
        while(low <= high){
            int mid = (low + (high - low)/2);
            if(matrix[mid/n][mid%n] == target){
                return true;
            }
            else if(matrix[mid/n][mid%n] < target){
                low = mid + 1;
            }
            else {
                high = mid - 1;
            }

        }
       return false;
```

Time Complexity : $O(log(n*m).$ Space Complexity : constant.

## Calculate ( n , x )

I/P : `( 2 , 10 ) .`
O/P : `1024` .
Brute Force approach .
Multiplying x n times and add up the answer .
Time Complexity $O(n).$ Space Complexity : $O(1).$
Optimal approach .
Intuition :

1. If n is even number then $n/2.$ and $x=x*x.$
2. if n is odd number then $n = n - 1.$ and $ans = ans * x .$

Time Complexity : $O(log_2n).$ if the power is even we reduce the number by n .

```cpp
double x ;
 int n ;
 cin>>x>>n;
 double ans = 1.0;
 long num = n ;
 if(num < 0) num = -1 * num;
 while(num > 0){
  if(num %2 == 0){
   num = num / 2;
   x = x * x ;
  }
  else {
   ans = ans * x;
   num = num - 1;
  }
 }
 if(n < 0) {
 ans = (double)1.0/(double)ans;
 }
 cout<<ans<<endl;
```

### Find the majority Element

Return that element which occurs more than ( n / 2 times ) where n is the length of the array .

I/P : `nums = [ 3 , 2 , 3] .`

O/P : `3 .`

Brute :

First we will traverse the array with two pointers i and j , where j traverse in a nested way.

count the occurrence of each element is the array .

If we found a count greater than n / 2 then we update our answer.

Time Complexity : $O(n^2).$ with constant space complexity .

Optimal :

We can use Hashing to store all the character’s frequency and traverse the hash table to find the required element.

Time Complexity : $O(n + n).$ Space Complexity : $O(n).$ for extra map we are using ( this much space complexity is only needed when the array contains all unque characters ).

> Note first O(n) in the time complexity can be $O(nlogn)$ depending upon which map we are using . in case of unordered map the best and average case is O(1) , where as worst case is O(n).

Most Optimal :

Moor’s Voting Algorithm

1. First we create two variables ele and count .
2. We select a random element as our ele and increase its count when we found that same element and decrease the counter when we found another element.
3. Once we found that count variable is zero then new update out element to current one and starts again.
4. When we reach end of the array and the count is not equal to zero , which means we have found our majority element.

> We need to traverse again to check weather the element is greater than ( size of array / 2 ).
> if not then return -1.

```cpp
vector<int> nums{3,2,3};
 int cnt = 0 , ele ;
 for(int i = 0 ; i< nums.size() ;i++){
  if(cnt == 0){
   ele = nums[i];
   cnt = 1;
  }
  else if(ele == nums[i]){
   cnt++;
  }
  else {
   cnt--;
  }
 }
 cout<<ele<<endl;
```

Time Complexity : $O(n).$ with constant Space Complexity .

## Rotate Matrix

![](https://i.imgur.com/KqQYG4c.png)

Brute Force :

Generate another matrix with the given formula.

$matrix[j][n-1-i]=grid[i][j]$

Time Complexity : $O(n^2)$

> Interviewer can ask you to not to use secondary array , just hinder the given one.

Optimal :
First we can transpose the matrix.
Reverse each row.

```cpp
class Solution {
public:
    void reverse(vector<int> &arr){
        int low = 0 , high = arr.size()-1;
        while(low <= high){
            int temp = arr[low];
            arr[low] = arr[high];
            arr[high] = temp;
            low++;
            high--;
        }
    }
public:
    void rotate(vector<vector<int>>& matrix) {
        for(int i = 0 ; i<matrix.size() -1 ; i++){
            for(int j = i+1 ; j<matrix.size() ; j++){
                swap(matrix[i][j],matrix[j][i]);
            }
        }
        // transposing of matrix is done
         for(int i = 0 ;i<matrix.size() ; i++){
             reverse(matrix[i]);
         }
    }
};
```

Time Complexity : $O(n^2 + n^2).$

## Merge Intervals

Very Important for interviews.

I/P : `intervals = [[1,3],[2,6],[8,10],[15,18]]`.

O/P : `[[1,6],[8,10],[15,18]]`

Approach :

1. Check for the base case i.e. only once intervals is given then return original interval ( as their can not be any other one).
2. Sort the intervals using inbuilt sort function.
3. While traversing the vector we implement this logic

```cpp
    if (currentInterval[1] >= intervals[i][0]) {
                currentInterval[1] = max(currentInterval[1], intervals[i][1]);
            } else {
                ans.push_back(currentInterval);
                currentInterval = intervals[i];
            }
        }
```

1. After the for loop we need to put the last currentInterval into our answer.
2. return the ans.

Time Complexity : $O(nlogn+n)$ , Space Complexity : $O(n).$

## Merge sorted arrays without extra space

I/P :
`N = 4, arr1[] = [1 3 5 7]`
`M = 5, arr2[] = [0 2 6 8 9]`

O/P :  
`0 1 2 3 5 6 7 8 9.`

Brute approach :

1. Create another array
2. Apply the merge algorithm
3. Change the original array with the merged array.

Time complexity : $O(n+m)$ , Space complexity : $O(n+m)$.

Optimal approach :

1. We will take two pointers left = n - 1 , right = 0.
2. Move both the pointers left and right

```cpp
while(left >= 0 && right <= m - 1){
               if(arr1[left]>arr2[right]){
                   swap(arr1[left],arr2[right]);
                   left--;
                   right++;
               }
               else {
                   // because we know that rest of the element will already be sorted
                   break;
               }
           }
```

1. sort both the arrays individually.

Time complexity : $O(min(n,m)+mlogm+nlogn)$, Space complexity : $O(1)$.

> In order to get the ceiling value of a division we can do this :
> Note the given example only works for division with 2

$$
ceil =   \left(  \dfrac{ L  }{ 2  }    \right)  + \left( Lmod2  \right)
$$

### Find the duplicate element

I/P : `nums = [1,3,4,2,2]`

O/P : `2`

Approach

Brute

1. Sorting and the array and then doing a linear search to find the duplicate element.

Time complexity : $O(nlogn + n)$ , here we are modifing the array.

Hashing

1. We store the frequency of each element in a hash map and return the key which has the frequency as 2 .

Time complexity : $O(n+m)$ where n is the size of the array and m is the size of the hashmap .

Optimal

We can use the fast and slow pointer approach

`slow = nums[slow]`

`fast = nums[nums[fast]]`

```cpp
int fast = nums[0];
        int slow = nums[0];
        do{
            slow = nums[slow];
            fast = nums[nums[fast]];
        }while(fast!=slow);
        fast = nums[0];
        while(fast!=slow){
            slow=nums[slow];
            fast=nums[fast];
        }
        return slow;
```

Time complexity : $O(n)$ , Space complexity : $O(1).$

## Return the missing and repeated number

I/P : `5
5 2 3 2 1`

O/P : `[4,2]`

Approach :

1. Brute force

   Count the occurrence of every number in the array using two for loops and if count is 2 then add to answer or if count is 1 then also add to the final answer.

   Time complexity : $O(n^2)$

2. Using hashing

   Time complexity : $O(n+n+n)$ , Space complexity : $O(n)$ .

   $$
    \dfrac{ n \cdot   \left( n+1  \right)    }{ 2  }
   $$

   $$
    \dfrac{ n \cdot   \left( n+1  \right)   \cdot   \left( 2n+1  \right)    }{ 6  }
   $$

```cpp
pair<int,int> missingAndRepeating(vector<int> &arr, int n)
{
   unordered_map<int,int> mp;
  for(int i = 1 ; i<=n ; i++){
    mp.insert({i,0});
  }
  for(int i = 0 ; i<n ; i++){
    mp[arr[i]]++;
  }
  pair<int,int> ans;
  for(auto it : mp){
    {
      if(it.second == 0){
        ans.first = it.first;
      }
    }

    if(it.second == 2){
      ans.second = it.first;
    }
  }
  return ans;
}
```

1. Using simple math

   First we get the sum of the n numbers using standard formula. and actual sum of n numbers using iterations.

   Then we get the sum of the squares of the n numbers using standard formula and actual sum of n numbers using iterations.

   Calculate the difference of the S - Sn .

   Calculate the difference of the S2 - S2n .

   Using $X^2 - Y^2$ = $(X-Y)(X+Y)$ .

   we update the second difference .

   calculate the first and second number by solving the given equations.

   ```cpp
   long long Sn = (n*(n+1))/2;
     long long S2n = (n*(n+1)*(2*n+1))/6;
     long long S =0, S2=0 ;
     for(int i = 0 ; i<n ; i++){
      S+=arr[i];
      S2+= (long long )arr[i] * (long long)arr[i];
     }
     long long val1 = S - Sn ;
     long long val2 = S2 - S2n;
     val2 = val2/val1;
     long long x = (val1 + val2)/2;
     long long y = x - val1;
     return {(int)y , (int)x};
   ```

   Time complexity : $O(n)$ , Space complexity : $O(1)$ .

### Count inversions

I/P :
`5`

`2 5 1 3 4`

O/P : `4`

Approach :

1. Brute force

   Do a nested for-loop

   `for ( i 0 to n -1 )
for ( j i+1 to n )
if(arr[i] > arr[j])
count++
return count`

   Time complexity : $O(n^2)$ , Space complexity : $O(1)$.

2. Merge Sort

   All the steps of the merge sort and then in the case when we are merging two arrays we need to add this line of code

   ```cpp
   while(left <= mid && right <= high){
     if(arr[left] < arr[right]){
      temp.push_back(arr[left++]);
     }
     else{
      cnt += (mid - left + 1);
      temp.push_back(arr[right++]);

     }
    }
   ```

   Time complexity : $O(nlogn)$ , Space complexity : $O(1)$.

## Maximum number of K sum pairs

Input : `nums = [1,2,3,4], k = 5`

Output : `2`

Approaches :

1. Brute Force

```cpp
class Solution {
public:
    int maxOperations(vector<int>& nums, int k) {
        int n = nums.size();
        int count=0;
        for(int i = 0 ; i<n-1 ; i++){
            for(int j = i + 1 ; j<n ; j++){
                if((nums[i]+nums[j]) == k){
                    nums[i] = -1e9;
                    nums[j] = -1e9;
                    count++;
                }
            }
        }
        return count;
    }
};
```

Very much brute 🥲 , Time complexity : $O(n^2)$. with constant space complexity : $O(1)$. 😜

1. Optimal

   Counting the occurrence of each element in the given array.

   For each element x we check weather k - x , exist in the array or not.

   if the a pair exist then
   `count += min(count(x),count(k-x))`

   `if x == k -x`

   `count += count(x)/2`

   ```cpp
   class Solution {
   public:
       int maxOperations(vector<int>& nums, int k) {
           unordered_map<int,int> mp;
           for(int i = 0 ; i<nums.size() ; i++){
               mp[nums[i]]++;
           }
           int count = 0;
           for(auto it : mp){
               if(mp.find(k-it.first) != mp.end()){
                   if(it.first != k - it.first){
                       count += min(mp[it.first],mp[k-it.first]);
                       mp[it.first] = 0;
                       mp[k-it.first] = 0;
                   }
                   else {
                       count += mp[it.first] / 2;
                       mp[it.first] = 0;
                   }
               }
           }
           return count;
       }
   };
   ```

   Time complexity : $O(n+n)$ , because insertion and .find method in unordered_map takes O(1) in average case .

   Space complexity : $O(n$) . n is the number of unique elements in the given vector.

   1. Using sorting

      First we will sort the array the take two pointers left , right.

      Move the left and right pointers according to our requirements.

      ```cpp

      int solve(std::vector<int> nums, int k) {
        std::sort(nums.begin(), nums.end());
        int left_ptr = 0;
        int right_ptr = nums.size() - 1;
        int count = 0;
        while (left_ptr < right_ptr) {
          int cur_sum = nums[left_ptr] + nums[right_ptr];
          if (cur_sum == k) {
            count++;
            left_ptr++;
            right_ptr--;
          } else if (cur_sum < k) {
            left_ptr++;
          } else {
            right_ptr--;
          }
        }
        return count;
      }
      ```

      Time complexity : $O(nlogn + n)$ , Space complexity : $O(1)$.

## Different ways to add parentheses

Input : `expression = "2-1-1"`

Output : `[0,2]`

Approach :

```cpp
vector<int> diffWaysToCompute(string exp) {
        vector<int> ans;
        for(int i = 0 ; i< exp.size() ;i++ ){
            if(exp[i] == '*' || exp[i] == '-' || exp[i] == '+'){
                vector<int> left = diffWaysToCompute(exp.substr(0,i));
                vector<int> right = diffWaysToCompute(exp.substr(i+1));
                for(auto x : left){
                    for(auto y : right ){
                        if(exp[i] == '*'){
                            ans.push_back(x * y);
                        }
                        else if(exp[i] == '-'){
                            ans.push_back(x-y);
                        }
                        else if(exp[i] == '+'){
                            ans.push_back(x+y);
                        }
                    }
                }
            }
        }
        if(!ans.size()){
            ans.push_back(stoi(exp));
        }
        return ans;
    }
```

## Remove duplicates from the array 2

Input : `nums = [1,1,1,2,2,3]`

Output : `5, nums = [1,1,2,2,3,_]`

Approach :

Two pointer approach

```cpp
int removeDuplicates(vector<int>& nums) {
        int l = 0 , r = 0 , n = nums.size();
        while(r < n){
            int count = 1;
            while(r+1 < n && nums[r] == nums[r+1]){
                r++;
                count++;
            }
            for(int i = 0 ; i<min(2,count) ; i++){
                nums[l] = nums[r];
                l++;
            }
            r++;
        }
        return l;
    }
```

Time complexity : $O(n)$ , Constant space complexity .
