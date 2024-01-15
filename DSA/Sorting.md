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

**Selection sort** :  
Recursive approach for selection sort.

```cpp
void selection_sort_recursive(vector<int> &arr, int beginIdx) {
  if (beginIdx == arr.size()) {
    return;
  }
  int minIndex = beginIdx;
  for (int i = beginIdx; i < arr.size(); i++) {
    if (arr[i] < arr[minIndex]) {
      minIndex = i;
    }
  }
  if (minIndex != beginIdx) {
    swap(arr[minIndex], arr[beginIdx]);
  }
  selection_sort_recursive(arr, beginIdx + 1);
}
```

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
We can check if in any single pass the array if no swapping is done then the array is already sorted and we can exit the algorithm.

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

After the above optimization the complexity of the code becomes $O(n)$ for best complexity only.

**Bubble recursive Approach** :

```cpp
void bubble_sort_recursive(vector<int> &arr, int endIdx) {
  if (endIdx == 0) {
    return;
  }
  for (int j = 0; j < endIdx; j++) {
    if (arr[j] > arr[j + 1]) {
      swap(arr[j], arr[j + 1]);
    }
  }
  bubble_sort_recursive(arr, endIdx - 1);
}
```

## Insertion sort

<span style='font-weight:bold;color:red;'>Takes a element and place it in its correct position</span>  
Imagine a deck of cards and you are sorting it.

[Insertion sort](https://youtu.be/yCxV0kBpA6M)

```cpp
void insertion(vector<int> &arr) {
  for (int i = 1; i < arr.size(); i++) {
    int temp = arr[i];
    int j = i - 1;
    while (j >= 0 && arr[j] > temp) {
      arr[j + 1] = arr[j];
      j--;
    }
    arr[j + 1] = temp;
  }
}
```

Time complexity : $O(n^2)$ for the worst case and the average case.  
But for best case when the array is already sorted then the nested while loop never gets executed and the overall time complexity is $O(n)$.

**Stable Sorting Algorithm** :  
The order of already sorted elements is maintained even after the sorting algorithm is applied.

_Bubble sort & insertion sort are stable but selection sort is not stable sorting technique._

## Merge Sort

It is based on Divide and Conquer technique.

Time complexity : $O(nlogn)$, for all the cases.  
Space complexity : $O(n)$ for the extra array used to store the array elements. ( Also auxiliary stack space also used because of recursion ).

**Merge Sort function** :

```cpp
void merge_sort(vector<int> &arr, int low , int high){
  if(low < high){
    int mid = low + (high - low)/2;
    merge_sort(arr,low,mid);
    merge_sort(arr,mid+1,high);
    merge(arr,low,mid,high);
  }
}
```

**Merge function** :

```cpp
void merge_sort(vector<int> &arr, int low , int mid , int high){

  int i , j , k;
  int n1 = mid - low + 1;
  int n2 = high - mid;
  vector<int> left(n1), right(n2);
  for(int i = 0 ; i<n1 ; i++){
    left[i] = arr[low + i];
  }
  for(int j = 0 ; j<n2 ; j++){
    right[j] = arr[mid + j + 1];
  }
  i = 0 , j = 0 , k = 0 ;
  while(i<n1 && j <n2){
    if(left[i] <= right[j]){
      arr[k] = left[i];
      i++;
    }
    else{
      arr[k] = right[j];
      j++;
    }
    k++;
  }
  while(i<n1){
    arr[k] = left[i];
    i++;
    k++;
  }
  while(j<n2){
    arr[k] = right[j];
    j++;
    k++;
  }
}
```

## Quick sort

The average case time complexity is $O(nlogn)$.

**The main task is** :

- To find the pivot element.
- Place the pivot element in its correct position.
- Once the pivot is placed at its correct position all the elements to its left are smaller then the pivot and all the element to the right are greater than the pivot element.

**Approach** :

```cpp

int find_pivot(vector<int> &arr, int low, int high) {
  int pivot = arr[low];
  int i = low, j = high;
  while (i < j) {
    while (arr[i] <= pivot && i <= high - 1)
      i++;
    while (arr[j] > pivot && j >= low)
      j--;
    if (i < j) {
      swap(arr[i], arr[j]);
    }
  }
  swap(arr[j], arr[low]);
  return j;
}

void quick_sort(vector<int> &arr, int low, int high) {
  if (low < high) {
    int pivot = find_pivot(arr, low, high);
    quick_sort(arr, low, pivot - 1);
    quick_sort(arr, pivot + 1, high);
  }
}
```

> Note pivot can be any element not just the first element.

Time complexity : $O(nlogn) , Space complexity is only the recursion stack space.
