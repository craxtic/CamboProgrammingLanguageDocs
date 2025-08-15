# `const` keyword

`const` is used to make variables immutable, which means that they can only 
be read but not modified.

```
const type variable_name = value;
```

#### Example
```
const float PI = 3.1415;
```
`PI` is now immutable. If you try to modify its value, it will result in compilation error.


## One thing about `const`

In Cambo, for primitive-typed variables that was declared with `const`, the compiler will automatically 
perform constant folding by substituting their literal value at usage site, which means the need for 
memory allocation can be eliminated.
