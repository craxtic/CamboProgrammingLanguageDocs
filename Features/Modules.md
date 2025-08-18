# Modules 
Cambo uses module system to let programmers organize code into reusable, self-contained units. Each module 
is declared at the top of a file using `module` keyword and can be imported into other files using `import` 
keyword.

**math.kh**
```
module math;

int sum(int a, int b){
  return a + b;
}

int square(int n){
  return n * n;
}
```

**main.kh**
```
import math;

int main(){

  int r1 = sum(1, 2);   // r1: 3 
  int r2 = square(3);   // r2: 9

  return 0;
}
```
In the above example, the module declaration and definition are in a single `math.kh` file. However, 
in many cases you may want to hide the moudule's implementation details. When the module is compiled into 
a library, its internal symbols may no longer be visible to users, making it difficult for them to 
understand and explore the moudule's API.   
Therefore, you may want to separate the interface from the implementation so that you can expose only the 
public API, and keep the internal logic private while providing a clear view of the module's available 
functionality.

**math.kh**
```
interface math;

int sum(int a, int b);
int square(int n);
```

**math_impl.kh**
```
module math;

int sum(int a, int b){
  return a + b;
}

int square(int n){
  return n * n;
}
```


**main.kh**
```
import math;

int main(){

  int r1 = sum(1, 2);   // r1: 3 
  int r2 = square(3);   // r2: 9

  return 0;
}
```

Everything is the same as before, you just simplly create a new file and use 
the keyword `interface` to specify that it's a module interface of math.


## Implementation Separation
If the module implementation seems too large to follow and maintain, you can also
separate the implementation into different files.

**sum.kh**
```
module math;

int sum(int a, int b){
  return a + b;
}
```

**square.kh**
```
module math;

int square(int n){
  return n * n;
}
```


**main.kh**
```
import math;

int main(){

  int r1 = sum(1, 2);   // r1: 3 
  int r2 = square(3);   // r2: 9

  return 0;
}
```

`sum()` and `square()` are now defined in two separate files, but as long as these 
two files has the line `module math;`, they are considered to be the same 
module. And you can `import math;` to use the `sum()` and `square()` just like before.


## Subodinate Module
A subordinate module is a module that exists within the scope of a parent module. 
Instead of separating the implementation, you group related functionality under 
a common namespace while keeping the module hierarchy clear.
- Parent module: top-level module that may contain muliple submodules.
- Subordinate module: nested module, and also may have more children modules.


Here, we have module interface **math.kh**
```
interface math;

interface algebra{
  float sqrt(float x);
  float cbrt(float x);
}

interface trigonometry{
  float sin(float x);
  float cos(float x);
}
```
- `algebra` and `trigonometry` have now become math's submodules.
- Each submodule must have its own implementation in a separate file;

**algebra.kh**
```
module math.algebra;

float sqrt(float x) { return 0; }
float cbrt(float x) { return 0; }
```

**trigonometry.kh**
```
module math.trigonometry;

float sin(float x) { return 0; }
float cos(float x) { return 0; }
```

**main.kh**

```
import math;

int main(){

  float r1 = sin(12);
  float r2 = sqrt(4);

  return;
}
```
- `import math;` will import everything including nested mudules. 
- But if you do `import math.trigonometry`, this will only import the trigonometry 
submodule of math.

```
import math.trignometry;

int main(){

  float r1 = sin(3.4); // OK
  float r2 = sqrt(4);  // Error: sqrt() not found!

  return 0;
}
```

### Separating Submodule Interfaces

**trigonometry.kh**
```
interface math.trigonometry;

float sin(float x) { return 0; }
float cos(float x) { return 0; }
```

**algebra.kh**
```
interface math.algebra;

float sqrt(float x) { return 0; }
float cbrt(float x) { return 0; }
```

**math.kh**
```
interface math;

import interface algebra;
import interface trigonometry;
```
- The compiler will try to look for any files that have `interface math.algebra` and 
`interface math.trignometry;`.

The implementation will be the same as we did in a single file.
- **algebra_impl.kh** must have `module math.algebra;`
- **trigonometry_impl.kh** must have `module math.trigonometry;`


## Selective Importing
Similar to importing the submodule such as `import math.trigonometry;`, 
selective import allows you to only import a particular functionality from a module and its modules if 
exist.


**math.kh**
```
interface math;

struct Vect2{
  // ...
};

interface trigonometry{

  float sin(float x);
  float cos(flost x); 
}
```

**main.kh #1** 
```
import math.Vect2;
import math.trigonometry.sin();
import math.trigonometry.cos();


int main(){

  Vect2 v = Vect(sin(12), cos(12));

  return 0;
}
```

- If it's a function, you must use suffix `()`.

**main.kh #2**
```
import math.Vect2;
import math.trigonometry.{ sin(), cos() };

int main(){

  Vect2 v = Vect(sin(12), cos(12));

  return 0;
}
```

- You can just wrap in `{}` to import in a single line without repeatition.


