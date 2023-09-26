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
## Bubble sort
```cpp
void bubblesort(std::vector<int> &nums) {
  int n = nums.size();
  for (int i = 0; i < n - 1; i++) {
    for (int j = i + 1; j < n; j++) {
      if (nums[i] > nums[j]) {
        std::swap(nums[i], nums[j]);
      }
    }
  }
}
```
Time complexity : $O(n^2)$ in for worst and average case. 
But we can do optimization 
```cpp
void bubblesort(std::vector<int> &nums) {
  int n = nums.size();
  for (int i = 0; i < n; i++) {
    bool didswap = 0;
    for (int j = 0; j < n - 1; j++) {
      if (nums[j] > nums[j + 1]) {
        std::swap(nums[i], nums[j]);
        didswap = 1;
      }
    }
    if (didswap == 0) {
      break;
    }
    std::cout << "Runs" << std::endl;
  }
}
```
After the above optimization the complexity of the code becomes $O(n)$ for best complexity. 
## Insertion sort
<span></s