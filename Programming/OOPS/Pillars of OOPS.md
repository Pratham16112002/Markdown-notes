
### Class
Blueprint or a set of instructions to build a specific type of object. 
It tell how the object behaves and what the object actually contains. 
### Object
Instance of class. 
It is just a self contained component which contains methods and properties to make particular type of data useful. 
## Static
It is used in memory management. 
If a variable is made static then it is executed before the main block is executed . 
Once a static block is executed then we can easily call static properties and methods without creating actual objects of class. 
### Virtual
Making a method virtual means you can override it in derived class. 
Used when you want to override a new method with the same signatures in a derived class . 
### Abstract
Used to declare a class or a method as abstract. 

> Do nothing function 
`void display()=0`
also called pure virtual function.
> 

Pure virtual function is used to make any class abstract . 
Abstract class is a special class which contains atleast one virtual function. 
To declare a class abstract : 
```cpp
public abstract class Employee {
}
```

### Final
Used to restrict the user . 
If you make a variable as final then  you cannot change the value of the final variable ( it will be constant ). 
If you make a method as final then you cannot override it. 
if you make a class as final then you cannot extend it further. 
### Explicit

Used to mark constructor to not implicitly convert types in C++.
To prevent implicit typecasting. 
```cpp
#include<iostream>
using namespace std;
class sample
{
public:
	explicit sample(int x){
		cout<<"Value of x is : "<<x<<endl;
	}
};

int main(int argc, char const *argv[])
{
	sample obj = 3.24;
	return 0;
}
```

## this

it is a reference variable that refers the current object. 
it is a pointer to the current object of the class which is being created. 

## Const

It is a way of declaring something , in such a way that it should not be modified . 
To take the variability of a variable. 
Same goes with the const, when its used with the methods then the method cannot modify the state of the object on which it is called. 

## Super

It is used to refer to the immediate parent class object. 
when ever we create an instance of the sub-class then instance of the parent class is created implicitly, which is referenced by super keyword. 
> Methods we cannot overload
1. Function template 
2. Member and Non-member function 
3. Function that differ only by return type
> 
### STL Algorithms
**all_of** : This method returns true , if all the elements in the iterator follows the lambda function specified in the parameter of all_of function.
```cpp
  std::cout << std::all_of(nums.begin(), nums.end(),
                           [](int x) { return x > 0; });
```
**any_of** : This method return true, if any of the element in the iterator follows the lambda function specified in the parameter of any_of function. 
### Lambda function
Creates an unnamed function object which is capable of capturing variables in scope.
Syntax : 
`[captures]<tparams> requires (params)specs{function body}`
**captures** : It specifies how the variables surrounding the scope is made available in the function body. 
There are two ways to capture variables : 
1. By reference : `[&variable]` or `[&}` means capture all variables with reference. 
2. By value : `[variable]` or `[=]` means capture all variables by value. 
**tparams** : specify template parameters in the lambda function. 
**specs** : to include specifies like , const , mutable or noexcept. 



