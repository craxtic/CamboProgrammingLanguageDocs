# Conditional Statements


## I. if statement

```
if(condition){
  
}
```

## II. if-else statement
```
if(condition){

}else{

}
```

```
if(condition_1){
  
}else if(condition_2){

}else{

}
```



## III. swtich statement
```
switch(condition){
  case value:
    // code block
  break;
  case value:
    // code block
  break
  default:
    // code block
  break
}
```
- `value` can only be of type integer, floating-point, character or boolean.


### Error Cases
- The `contidion` must be a boolean expression; assigments are not allowed.
```
int number;
if(number = 1){

}
```
This will result in compilation errors