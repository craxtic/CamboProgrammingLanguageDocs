## Compile Time
```
@compile-time
```

```
@compile-time
// multi-line
@end
```

The `@compile-time` annotation is used to tell the compiler that the marked line or code block below should be 
run at compile time, unless the code is run-time only such as functions that can only be called at run time.
- it will reduce some memory usage.
- it wlll reduce the execution time at run time.
- but it will increase the compilation time.

### Example #1
```
void sum(int a, int b){
  return a + b;
}

int main(){

  @compile-time
  int c = sum(1, 2);
  
  return 0;
}
```
The compiler will compute the `sum` at compile time and it will assign 3 direcly to `c`. 
No run-time calculation will be performed. 


### Example #2
You can also use `compile-time` annotation with if statements, loops, functions, etc, 
literally anything you think it can be run at compile time.
```
@compile-time
for(int i = 0; i < 5; i++)
  print(i);
@end
```

this is the actual code in the final executable
```
print(0);
print(1);
print(2);
print(3);
print(4);
```
The compiler just repeatedly generates the function calls `print` with the actual value 
of `i`. This way you can save 4 bytes of memeory and eliminate the process of 
comparing `i < 5` and increasing `i++`. 

### Example #3
You can also marked an entire function as `@compile-time`, but should not be the `main` one, lol.

```
@compile-time
int sum(int a, int b){
  return a + b;
}
@end

int main(){

  printf(sum(1, 2));

  return 0;
}
```
This is similar to example #1 but now the `sum` is forever compile-time. `print(3)` will be generated.
- note: `sum` now can only accept any arguments that are known at compile time, otherwise will result 
in compilation error.
In order to clarify this note, here is another two examples:
```
int main(string argv[]){

  @compile-time
  string myString = argv[1];

  return 0;
}
```
This will surely result in compilation error, becuase `argv[1]` is clearly unknown at compile time.  
Here another example and important one.

```
int main(){

  int a = 1;

  @compile-time
  int b = a;

  return 0;
}
```
The compiler will throw an error because the value of `a` is not fixed, can be changed anytime, making it 
unknown at compile time. To solve this, you can make `a` a fixed variable by using `const int a = 1;`.


## Other Usages
`@compile-time` annotation is really useful when the goal is to produce and executable optimized for speed and 
performance. But, what's more important is that `@compile-time` plays a significant role when working with 
variadic functions. See [Variadic Function](VariadicFunction.md)
