# Bit Manipulation

^ ⇒ XOR operator. 

~ ⇒ Negation operator. 

Computer stores the integers in two’s compliment representation , positive number is presented as itself , but negative number is represented as two’s complement of its absolute value. 

### Finding 2’s Complement

1. First find the 1’s complement of the binary number. 
2. add 1 to the 1’s complement . 

When we access a negative number in computer memory , first we check the sign bit of the binary representation stored in the memory , if the sign bit is set then it means that the number is negative and we will again calculate its 2’s complement to get the number. 

<< ⇒ Left shift operator.  

Left shift by 1 is like multiplying by 2 , Left shift by 2 is like multiplying by 4 .  

>> ⇒ Right shift operator. 

Right shift by 1 is like dividing by 2 , Left shift by 2 is like dividing by 4. 

Arithmetic 

Arithmetic left shift is equivalent to the Logical left shift , the vacant least significant bit is filled with zero and most significant bit is discarded. 

Arithmetic right shift , the vacant least significant bit is filled with bit equivalent to the previous MSB. 

### Bit set or not

To check weather the $ith$  bit is set or not . 

$(numAND(1<<i)!=0)$. 

if the above condition is true then the particular bit is set , else the bit is not set. 

### Setting a bit

To set the $ith$ bith . 

$num OR (1<<i)$

If we apply the above operation then the bit at $ith$  position will be set. 

### Clear bit

To remove a set bit from the given number at a specific position. 

```cpp
int clearBit(int n , int i){
	int mask = ~(1<<i);
	return n & mask;
}
```

### Update Bit

Updating a particular bit value at a particular position . 

```cpp
int mask = ~(1<<i);
	n = n & mask;
	n = n | (newVal<<i);
	return n;
```

## Find the xor sum of n elements

If we try to find out  xor pattern of all the elements with % 4 , then we see a pattern. 

```cpp
if (n % 4 == 0)
    {
        std::cout << n << std::endl;
    }
    else if (n % 4 == 1)
    {
        std::cout << 1 << std::endl;
    }
    else if (n % 4 == 2)
    {
        std::cout << n + 1 << std::endl;
    }
    else
    {
        std::cout << 0 << std::endl;
    }
```

By using the above operation we can find xor of n elements with constant operation. 

### Remove the last set bit

`N & ( N -1 )` 

**IMPORTANT**

### Check weather the number is a power of 2

if ( n & ( n -1 ) == 0 ) then it is a power of 2 . 

## Count the number of set bits

Brute force : 

```cpp
int count = 0;
while(n!=0){
	if(n&1 == 1){
		count++;
	}
	n = n>>1;
}
return count;
```

Time complexity : $O(n)$ , where n is the number of bits. 

Optimal : 

```cpp
int n = 14;
    int count = 0;
    while (n != 0)
    {
        n = n & (n - 1); // Turning off the right most bit
        count++;
    }
    std::cout << count << std::endl;
    return 0;
```

Time complexity : $O(n)$ , where n is the number of set bits.