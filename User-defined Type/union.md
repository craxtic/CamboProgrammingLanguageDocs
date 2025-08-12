# Union
A union is a user-defined type that allows different data types to be stored in the same memory location.

```
union identifier{
  type variable_name,
  type variable_name,
  ...,
  type variable_name,
};
```

- The size of a union will depend on one of its member with the largest size.

#### Example
```
union data {
  int i;
  float f;
  double d;
}
```
In this case, since double has the biggest one, which is 64 bits, 
the size of memory allocated for this union will be 64 bits.



