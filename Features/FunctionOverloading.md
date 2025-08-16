# Function Overloading
Overloaded functions are funtions that share exact same name but different parameters. And each function 
has its own unique signature. A signature is the combination of the function's name and parameters.    
signature = name + parameters  

#### Example
```
int add(int a, int b){
  return a + b;
}

int add(int a, int b, int c){
  return a + b + c;
}
```
In this example, we define two functions sharing the same name, but each has different signature because
of the different parameters. And you can define many functions sharing the same name as many as you want 
as long as they have different parameters.  
  

Now look at another example

```
int add(int a, int b){
  return a + b;
}

float add(int a, int b){
  return a + b;
}
```
However, this will cause compilation error becuase two functions sharing the same signature exist at the 
same scope. Although they have different return types, it does not change the function signature as long as 
the parameters stay the same.  
   
**Note**: the parameters only make the signiture different when:
- changes in types
- changes in order of types

```
int add(int a, int b){
  return a + b;
}

int add(int x, int y){
  return x + y;
}
```
The identifiers of the parameters have no effect on the signature. This will result in compilation error.

