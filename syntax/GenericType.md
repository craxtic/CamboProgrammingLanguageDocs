# Generic Type
Generic programming is a feature that enable us to write a generic code for functions or structs that can 
be used with any types of data. In Cambo, when a generic function or struct is used with a specific type, 
the compiler generates a concrete version of the function or struct tailored to that type at compile time. 
This means you don't have to write all the versions you need, just write a generic one and the compiler
will automatically do the job for you. This can be achieved by using the `type` keyword and `<>` sign.


```
struct struct_name<type T1, type T2, ..., type Tn> {
  
}
```

```

return_type function_name<type T1, type T2, ..., type Tn>(parameters){

}
```
- `type` is a keyword.
- `T1, T2, ..., Tn` are identifiers.
- **syntax is still in consideration.**


#### Example #1
```
struct Box<type T>{
  T _value;

  init Box(T value){
    self.value = value;
  }

  void show(){
    print("value: {}", self.value);
  }


}

int main(){

  Box<int> box1 = Box<int>(10);
  Box<float> box2;
  box2.value = 13.13;
 
  box1.show();
  box2.show();

}
```
```
Box<int> box; // OK
Box box;      // error

Box<int> box = Box<int>(10); // OK
Box<int> box = Box(10);      // OK
Box box = Box<int>(10);      // error
Box box = Box(10);           // error
```


#### Example #2
```
T sum<type T>(T a, T b){
  return a + b;
}

int main(){

  int r1 = sum<int>(1, 2);
  float r2 = sum<float(1.1, 2.2);

  return 0;
}
```

In both example #1 and #2, at the line  
`Box<int> box1 = Box<int>(10);`,  
`Box<float> box2;`,  
`sum<int>(1, 2)` and  
`sum<float>(1.1, 2.2)`,  
the compiler will create a concrete version of each struct and function based on the specified type.  
The generic `struct Box<type T>` and `T sum<type T>(T a, T b)` serve as blueprints for the compiler. 
   
For example: when the compiler sees this `sum<int>(1, 2)`, it will generate a new function 
`sum()` with type `int` at compiler time.
```
int sum(int a, int b){
  return a + b;
}
```
- All type `T`s are replaced by type `int`.


