# Structure `struct` in Cambo

`struct` is a user-defiend type that groups serveral related pieces of data together, similar to struct in 
C. However, in Cambo, `struct` is more than just a data container. It can also contain functions that 
operate on its data.

### Key Features
- **Fields**: Store the data of the struct. All data are external by default.
- **Encupsulation**: Both Fields and Functions can be declared for internal use only by adding `_` 
before variables or functions name.
- **Methods**: Functions attached to the struct itself. They, by default, have access to the struct 
instance through the keyword `self`; 
- **Construtor**: Defined using `init` keyword, this is a special function which is automatically invoked
when an instance of the struct is created.
- **Destructor**: Defined using `deinit` keyword, this is a special function which is automcatically 
invoked when a struct instance goes out of scope.
- **Static**: static members are tied to the struct itself, not individual instances. It can be called 
shared memebers;
- **This is not OOP**: While the syntax seems like OOP, however, it's not. It's just `struct` with extra 
features, no inheritance or polymorphism is supported.

```
struct struct_name{
  type variable;  // public variable, can be accessed from outside.
  type _variable; // private and should only be used internally. 

  init struct_name(parameters){
    // constructor
  }

  deinit struct_name(){
    // destructor
  }

  type function_name(parameters){
    // function
  }

};
```


#### Example
```

struct Vect2{
  double x;
  double y;

  init Vect2(double x, double y){
    self.x = x;
    self.y = y;
  }

  deinit Vect2(){
    print("Destroying Vect2\n");
  }

  Vect2 copy(){
    return Vect2(self.x, self.y);
  }

  static double dot(Vect2 a, Vec2 b){
    return (a.x * b.x) + (a.y * b.y);
  }

};

int main(){

  {
    Vect2 v1 = Vect2(1.1, 2.2);
    Vect2 v2 = Vect2(3.3, 4.4);
    double dot_product = Vect2.dot(v1, v2);

    Vect2 v3 = v1.copy(); 
  }

  return 0;
}
```

- This is interestingly just a `struct`, no fancy object-oriented programming.
- When they go out of scope, after `{}` (for demonstration), the `deinit()` will be called.
- We can also explicitly call the `deinit()` manually, for example `v1.deinit();`.


### WHY #1

Why uses this long syntax
```
init struct_name(){}
```
instead of this shorter one 
```
init(){}
```
The answer is to improve readability. In some cases, the code is overwhemingly large, so programmers can 
clearly know what struct the `init()` and `deinit()` belongs to. It helps just a little but it does help, 
particularly `deinit()` because it's often defined at the end of the struct.
