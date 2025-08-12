# Loop

The `contidion` must be a boolean expression; assigments are not allowed.

## I. While Loop
```
while(condition){

}
```

#### Example
```
while(2 < 4){
  print("always run");
}
```

## II. For Loop

```
for(initialization; condition; updation){ 
}
```


#### Example
```
for(byte i = 0; i < 10; i++){
  print("always run");
}
```

## III. Repeat While Loop
`repeat-while` loop is entirely the same as `do-while` loop in C/C++, 
but I just want to change the word `do` to `repeat` which sounds more natural.

```
repeat {

}while(condition)
```

#### Example 
```
int i = 0;
repeat{
  print("hello, new world\n");
  i++;
} while(i < 10);
```
