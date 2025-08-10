# Array

An array is a fixed-sized sequential collection of elements of the same data type. 
Its size must be known at compile time.

- Index of an array always starts from 0 -> n.

## I. One Dimensional Array


### Case 1
```
type array_name[size];
```
- Without initialization, all elements will be set to their default values, mostly zero/null/false.

### Case 2
```
type array_name[size] = {element, element, ..., element};
```
- The number of elements must equal to `size` 


### Case 3
```
type array_name[] = {element, element, ..., element};
```
- The size of the array will be automatically counted at initialization.

#### Example
```
int first_list[2];
first_list[0] = 9;
first_list[1] = 10;

int second_list[2] = {9, 10};   // there can't be more than 2 elements
int third_list[] = {9, 10, 11}; // add more elements as many as you want 
```


## II. Two Dimensional Array
A 2D array is an array of an array. :]
### Case 1
```
type array_name[row_size][column_size];
```
- Without initialization, all elements will be set to their default values, mostly zero/null/false.

### Case 2
```
type array_name[row_size][column_size] = {
  {element, element, ..., element},
  {element, element, ..., element},
  ...
  {element, element, ..., element},
};
```
- All number of the rows must equal to row_size
- All number of the elements in each row must equal to column_size


### Case 3
```
type array_name[] = {
  {element, element, ..., element},
  {element, element, ..., element},
  ...
  {element, element, ..., element},
};
```
- The size of the array will be automatically counted at initialization.
- The number of all rows must be the same.

#### Example
```
int matrix[2][3] ={
  {1, 2, 3},
  {4, 5, 6}
}

print(matrix[0][0]); // output: 1
print(matrix[1][1]); // output: 5
```


## III. Constant Array
A constant array is an array which all of its elements can not be modified.

```
const type array_name[size] = {element, element, ..., element};
```
- A const array must be always initialized, otherwise will result in compilation error.
- `size` is optional.

#### Example
```
const int magic_number[] = {45, 23, 75, 12, 86};
magic_number[0] = 54; // will result in compilation error!
```

