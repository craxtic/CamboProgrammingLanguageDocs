# Functions


## I. Normal function definition
```
return_type function_name(parameter_list){
  // function body
} 
```
### Overview
- Parameter list is optional.
- Keyword `return` is used for returning a value from a function and the value must have the same type as `return_value`.
- Keyword `void` is used for specifying that function returns nothing.
### Compilaton Error Cases
- Attempting to return a value that is not the same type as `return_type`.
- Attempting to return a value, where `void` is used as the `return_type`.
- Attempting to return a reference to a stack-allocated local variable, which becomes invalid after the function returns.



#### Example
```
int add(int a, int b){
  return a + b;
}

void do_nothing(){
  return;
}


int main(){
  do_nothing();
  int result = add(1, 2);
  return 0;
}

```




## II. Default Value Parameters

```
return_type function_name(type param_name = default_value){

}  
```
- Default value must be constant, which is known at compile time.
- A parameter with default value will become optional, can be skipped when the function is called
- All default value parameters should be defined at the end of parameter list

#### Example
```
float scale(float a, float factor = 1.0){
  return a * factor;
}

int main(){

  float r1 = scale(3.0);       // r1 = 3.0 * 1.0 = 3.0
  float r2 = scale(3.0, 1.5);  // r2 = 3.0 * 1.5 = 4.5

  return 0;
}
```

## III. Callback

See [Lambda Expressions](Lambdas.md) first!

### syntax

```
return_type function_name(return_type(parameter_types) callback_name){

}
```

#### Example 
```

struct Button {

  void() clickHandler;

  void onClick(void() handler){
    self.clickHandler = handler;
  }
}

// simulate button click
void clickButton(Button *button){
  button.clickHandler();
}

int main(void){


  Button button = Button();

  button.onClick(() => {
    print("hello, button!\n");
    print("hello, world!\n");
  });

  // now we can click the button
  clickButton(&button);

  return 0;
}
```

This code above is just for demonstration, a real button is much more than that.   








## IV. Function definition with error handling.
```
return_type function_name(parameter_list) error_type {
  // function body
}
```
See [Error Handling](ErorrHandling.md)
