## Selection sort
<span style='font-weight:bold;color:red;'>Select minimum & swap</span>
Unsorted part will decrease in length also sorted part will also increase further. 
```cpp
void help(std::vector<int> &nums) {
  int n = nums.size();
  for (int i = 0; i < n - 1; i++) {
    int mini_index = i;
    int maxi = nums[i];
    for (int j = i; j < n; j++) {
      if (nums[j] < maxi) {
        maxi = nums[j];
        mini_index = j;
      }
    }
    if (mini_index != i) {
      std::swap(nums[i], nums[mini_index]);
    }
  }
}
```
Time complexity : $o(n^2)$ for all best , average and worst case.


