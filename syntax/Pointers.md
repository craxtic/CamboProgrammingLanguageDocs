# Pointers in Cambo
A pointers is simply a variable that store the memory address of another 
variable. Instead of holding a direct value, it holds the location in the  
computer's memory where the actual value is stored.

```
type* pointer_name;
type *pointer_name;
type * pointer_name;
```
All are OK as long as the asterisk `*` stays in the middle.


## Dereferencing
```
int num = 13;
int *ptr = &num;

print("address: {}\n", ptr); // this will output the memory address: 0x3454...
print("value: {}\n", *ptr);  // this will output the value stored at that memeory address: 13
```
  

## Pointer Arithmetic
Unlike normal maths arithmetic, only addition `+` and substraction `-` are allowed 
for pointer arithmetic.

```
ptr++;
ptr--;
ptr += n;
ptr -= n;
ptr1 = ptr2 + n;
ptr1 = ptr2 - n;
```

Everything is just the same as C.  
Any changes or new features will be updated later.

