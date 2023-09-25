#### What are pointers ? 
It is a integer variable which stores the memory address.

>Types does not matter while storing pointers. 

```cpp
#include <bits/stdc++.h>
#include <iostream>

int main() {
  int x = 10;
  int *p = &x;
  void *p_void = &x;
  std::cout << p << std::endl;
  std::cout << p_void << std::endl;
  return 0;
}
```
In the above code the output of the code is same. 
![](https://i.imgur.com/67sWUfJ.png)
<span style='color:red;'>When updating the data the then the type of the pointer matters</span>
```cpp
int main() {
  int x = 10;
  int *p = &x;
  void *p_void = &x;
  *p_void = 12; // gives error
  std::cout << p << std::endl;
  std::cout << p_void << std::endl;
  return 0;
}
```
The above code is giving me a error, because I am trying to write a value of void pointers. 
