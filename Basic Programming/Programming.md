# Programming

> All the default parameters of the function are defined at the end among all the parameters.
> 
> 
> ```cpp
> int Sum(int a, int b = 2, int c = 3); Just Like this one. 
> ```
> 

### Function prototype

it is tells the program information about the function such as arguments passed and method return type and method name. 

```cpp
return_type function_name( datatype_1, dataype_2, ....)
```

> Note main() function can never have default parameters.
> 

## Singleton Class

The primary purpose of the singleton class is to limit the number of object creation to only one. 

Helps to prevent memory space wastage. 

## Lower Bound

`lower_boud()` method in c++ is used to return an iterator pointing to the first element in the range[first , last] , which has a value less than value. 

```tsx
int indx = lower_bound(temp.begin(),temp.end(),nums[i]) - temp.begin();
```

## Virtual Function

Those functions whose behavior can be overridden in derived classes.

Indicate the compiler to call the destructor method of the derived classes too , to prevent memory leak . 

 

```cpp
class Base 
{
public:
	Base() { cout << "Base Constructed\n";}
	virtual ~Base() { cout<<"Base Destructed\n";}
};

class Derived : public Base {
public:
	Derived() { arr = new int[5]; cout<< "Derived Constructed\n";}
	~Derived() { delete arr; cout<< "Derived Destructed\n";} 
private:
	int* arr;
};

int main(int argc, char const *argv[])
{
	Base *base = new Base();
	delete base;
	cout<< "----------------------" <<endl;
	Derived *derived = new Derived();
	delete derived;
	cout<<"------------------------" <<endl;
	Base* thomas = new Derived();
	delete thomas;
	return 0;
}
```

## Union in C programming

It is a user defined data type , allow us to combine different data types together. 

```cpp
union {
int a;
float b;
}x;
```

> The main difference between union and struct is that memory allocated to struct = data1.size + data2.size + ….. , memory allocated to union = max( data1.size , data2.size , … ) .
> 

## Repeat Function

In Javascript repeat function return a string with a specific number of copies. 

```jsx
{'hello'.repeat(100)}
// hello will treated as hello 100 times. 
```

REPT function is a text function that allows you to repeat a specific text string a specified number of times, In MS Excel. 

Shift + Space is the key combination used to select a row in MS Excel. 

Ctrl + Shift is the key combination used to select a column in MS Excel. 

MS Power point is the application have a conditional formatting option. 

In MS Word you can insert a page in both Header and Footer. 

In MS Power point Ctrl + D is used to duplicate a slide. 

Modifier key used to change the selected text in bold 

→ Ctrl , Ctrl + B 

Q : How will you update the values of the formula cells if auto calculate mode of the excel is disabled  ?

A : F-9

Q : To delete a word to the right of the cursor ? 

A : Ctrl + Delete 

Microsoft Azure is providing the BLOB storage device ( Binary large Object type ). 

DES encryption algorithm is an example of Bit-oriented cipher. 

AES encryption 

128 bits → 10 rounds 

256 bits → 14 rounds 

192 bits → 12 rounds 

Google Cloud and IBM does not provide hybrid storage. 

The power point view that display only text ( title and bullets ) → Outline view . 

Q : In MS Power point header and footer button are found in which group ? 

A : Text group 

Tile slide is the slide that is used to introduce the topic and set the tone of the presentation . 

Asymmetric key cryptography depends upon the number of key bits. 

Macros  is the feature in MS Word that can speed up editing or formatting . 

Shift + Enter is the shortcut key for line break. 

## Roman to integer

Logic for conversion of roman to integer. 

```cpp
unordered_map<char,int> mp = {
	{'I' , 1},
	{'V' , 5}, 
	{'X' , 10},
	{'L' , 50},
	{'C' , 100},
	{'D' , 500},
	{'M' , 1000}
};

int romanToInt(string roman){
  int n = roman.size();
  int res = 0;
  for (int i = 0; i < n - 1; i++) {
    if (roman[i + 1] > roman[i]) {
      res -= mp[roman[i]];
    }
    res += mp[roman[i]];
  }
  res+=mp[roman[n-1]];
  return res;
}
```

Time complexity : $O(n)$ , where n is the length of the roman string. 

## Goldbach’s conjecture

> Even integers can be expressed an sum of two prime numbers .
> 

```cpp
bool isSumOfKPrime(int N, int k)
{
    if (N < 2 * k)
    {
        return false;
    }
    if (k == 1)
    {
        return isPrime(N);
    }
    if (k == 2)
    {
        if (N % 2 == 0)
        {
            return true;
        }
        return isPrime(N - 2);
    }
    return true;
}
```

Time complexity : $O(n)$  , in the worst case if n is prime number. 

```cpp
int n = 35;
    std::vector<int> prime_factors;
    for (int i = 2; i * i <= n; i++)
    {
        while (n % i == 0)
        {
            prime_factors.push_back(i);
            n /= i;
        }
    }
    int max_ele;
    if (n > 1)
    {
        max_ele = n;
    }
    max_ele = *max_element(prime_factors.begin(), prime_factors.end());
    std::cout << "The highest prime factor will be :" << max_ele << std::endl;

    return 0;
```

Time complexity : $O(sqrt(n))$.

## Optimal approach to find is

- First we create a sieve array like this :
    
    ```cpp
    const int N = 1000000;
    int sieve[N + 1];
    
    void createSieve()
    {
        for (int i = 1; i <= N; i++)
        {
            sieve[i] = i;
        }
        for (int i = 2; i * i <= N; i++)
        {
            if (sieve[i] == i)
            {
                for (int j = i * i; j <= N; j += i)
                {
                    if (sieve[j] == j)
                    {
                        sieve[j] = i; // it should be i, because i is the smallest number that it can divide
                    }
                }
            }
        }
    }
    ```
    
    Time complexity : $O(n + loglogn)$ .
    
- We can find the prime factorization in this way :
    
    ```cpp
    while(n!=1){
    	print(n);
    	n /= sieve[n];
    }
    ```
    
    Time complexity : $O(logn)$ . 
    

## **Permutation of first N positive integers such that prime numbers are at prime indices**

Note from 1 to N , there are K prime number and K prime indices , so there exist K! permutation and for non - prime number and indices , there exist ( N - K )! 

So total Permutation will be $K!*(N-K)!$.