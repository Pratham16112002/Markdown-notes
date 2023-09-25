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

## New 
It is not a keyword its a operator.
The main purpose of this keyword is to allocate memory in heap. 
The size allocated is dependent what we write after the new keyword. 
```cpp
char* buffer = new char[8]; 
```
👆Above code will specify 8 bytes of memory, because each character takes 1 bytes of memory. 
The above raise a system call  to check weather 8 bytes of memory is available in the memory, once found the this keyword return pointer to that memory location. 

It also calls the constructor of the class on the which new keyword is being called on. 
```cpp
Entity *entity1 = new Entity();

Entity *entity2 = (Entity *)malloc(sizeof(Entity));

```
The first line will call the constructor defined in the Entity class where as the second line will not call the constructor but will allocate the memory in heap. 
