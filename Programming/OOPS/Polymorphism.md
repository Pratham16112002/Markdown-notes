# Polymorphism

Polymorphism is a concept in which one task can be performed in many ways. 

Derived from two greek words **Poly : many , morphism : forms** . 

### Need

Polymorphism becomes really help-full when there exist multiple classes , which uses the same class functionality defined in the super class. 

Allows object of different class to be treated as the object of the same base class. 

## Function overloading

If we create two member function having the same name but different number or type of arguments .

Constructors can also be overloaded. 

it increases the readability of the program because you don’t need to use different names for methods that performs similar actions. 

## Compile time polymorphism

It is a process in which call to an overloaded method is resolved at the run time rather than at run time. 

### Ambiguity

```cpp
#include<iostream>

class Cal {
public:
	static void add(int a , long b){
		std::cout<<"The first method"<<std::endl;
	}
	static void add(long a , int b){
		std::cout<<"The second method"<<std::endl;		
	}
};

int main(int argc, char const *argv[])
{
	Cal c ;
	std::cout<<c.add(8,8)<<std::endl;
	return 0;
}
```

Gives a compile time , because compiler is confused which add method should be used in this case. 

> Note Function with same name but different return type cannot be overloaded , static and a non static member function of the same class cannot be overloaded.
> 

### Operator overloading

Part of compile time polymorphism. 

It is the idea of giving special  definition to an existing operator  without changing its original meaning. 

We can make operators work for user defined classes. 

```cpp
#include <bits/stdc++.h>

using namespace std;

class Complex
{
private:
    int real, img;

public:
    Complex(int r = 0, int i = 1)
    {
        real = r;
        img = i;
    }
    Complex operator+(Complex const &obj)
    {
        Complex res;
        res.real = real + obj.real;
        res.img = img + obj.img;
        return res;
    }
    void print()
    {
        cout << real << " + i " << img << endl;
    }
};

int main(int argc, char const *argv[])
{
    Complex c1(5, 6), c2(8, 9);
    Complex c3 = c1 + c2;
    c3.print();
    return 0;
}
```

In the above code the + ( which is a user defined operator works only on pre defined data type ) now it also works on user defined data type or class objects also. 

Operators like `::` , ( class member access operator ) `.,*`, `sizeof` ,  `? , :`  . 

## Run-time polymorphism

In this call to an overridden method is resolved at runtime rather than compile time. 

In this the overridden method is called through the reference variable of a superclass. 

## Virtual functions

It is a member function of the base class with is redefined in the derived class. 

It is function that is overridden in the derived class and instructs compiler to to execute late binding on that function , A function call resolved at runtime in late binding. 

```cpp
class Entity
{
public:
    virtual std::string getName()
    {
        return "Entity";
    }
};

class Player : public Entity
{
public:
    std::string m_name;

public:
    Player(const std::string name)
    {
        this->m_name = name;
    }
    std::string
    getName()
    {
        return m_name;
    }
};
```

## Virtual base class

It is used in a class to prevent multiple instance of that class in the case of multiple inheritance. 

```cpp
class A
{
public:
    void show()
    {
        std::cout << "Hello from A" << std::endl;
    }
};

class B : public A
{
};
class C : public A
{
};
class D : public B, C
{
};

int main(int argc, char const *argv[])
{
    D obj;
    std::cout << obj.show() << std::endl;
    return 0;
}
```

Solution : declare the class A as virtual .