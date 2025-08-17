# Lambda Expressions
A lambda expression is a convenient way to define an anonymous function object 
which can either be used inline or passed as an argument.

### syntax #1
```
(parameters) => expression
```

### syntax #2
```
(parameters) => {

}
```


Since lambdas are objects, they need a special data type to store them. Function pointers can be used for 
this, however it might be a bit verbose. Therefore, a new syntax is introduced. 

```
return_type(parameter_types) lamda_name;
```
For example:
- `int()` stores a lambda that returns value as an `int` and has no parameter.
- `void(int)` stores a lambda that return nothing and has one `int` parameter.


#### Lambda Example
```
int main(){

  int(int, int) add = (int a, int b) => a + b;
  int(int) square = (int n) => n * n;
  void() hello = () => {
    print("hello, pig\n");
    print("hello, cow\n");
    print("hello, chicken\n");
  }

  print("result: {}\n", add(2, 3));
  print("result: {}\n", square(2));
  hello();

  return 0;
}
```


**Note**:
```
void(int, int) add = (int a, int b) => a + b; 
```
This case will cause a compilation error because this `add` suppposes to return nothing. 
To solve the problem, `=> {}` code block should be use instead.
(add function is a bad example anyway, but I think you get the point.)


## Closure
In Cambo, any variables used in the lambda are captured automatically. But lambdas do not capture all the 
variables or objects in the scope, they only capture the ones that are used and also by value by default, 
meaning modifying the captured will not affect the outer variables.

```
int main(){

  short x = 1000;
  short y = 2000;
  int count = 1;

  // only `count` is captured by the lambda.
  void() counter = () => {
    count++;
  }

  print("old count: {}\n", count);  // output: 1
  counter();
  print("new count: {}\n", count);  // output: 1

  return 0;
}
```
In the above example, count still stay the same as before.

In order to capture by reference, we have to write some a more verbose syntax but worth it.
```
[]() => expression;
[]() => {code block}
```
You might be thinking this is even scarier than `[](){}` in C++ becuase of one additional `=>`, just kidding.  
Similar to lambda in C++, `[]` is used to capture outer variables. However, in Cambo, it's used to 
capture by reference only (by value is done by default without using `[]`).


#### Example: Capturing By Reference
```
int main(){

  short x = 1000;
  short y = 2000;
  int count = 1;

  
  void() counter = [count]() => {
    count++;
  }

  print("old count: {}\n", count);  // output: 1
  counter();
  print("new count: {}\n", count);  // output: 2


  return 0;
}
```
Only `count` is captured by reference in the lambda. If x or y is used, they will be still captured by value.
   
But there's a way to caputured everything by reference. We can achieve this by using `[&]`.

```
void() counter = [&]() => {
    count++;
  }
```

When `[&]` is used instead, every outer variable used in the lambda will be all captured by reference 
and no by value will be possible.


**keyword proposal**: `lambda`
- We use `lambda` keyword to tell the compiler to inference the type for us automatically.
- No need to write these things `void(int, int)`, `int(float, string)`, etc. 