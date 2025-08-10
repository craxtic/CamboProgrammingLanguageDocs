# Enumeration

An enum is a special type that represents a group of constants.

```
enum identifier{
  constant = value,
  constant = value,
  ...,
  constant = value
};
```

```
enum identifier{
  constant,
  constant,
  ...,
  constant
};
```
- `constant` will automatically start with the value of zero if not specified.  



#### Example
```
enum Level { Low, Medium, High };

Level current_level = Level.Low;
```

### Note
- Enums are strongly typed. 
- Although each constant represents an integer value, enum values cannot be assigned to variables of different enum type.
- Two enum values with the same integer value are not considered equal if they belong to different enum types.

```
enum Level {Low, Medium, High};
enum Color {Red, Yello, Green};

Level current_level = Level.Low;
if(current_level == Color.Red){
  // false condition!
}

current_level = Color.Red;
// this will result in compilation error!
```
`Level.Low` and `Color.Red` holds the same integer value, 0. But the condition will never be true because they belong to different enum type, Level and Color.

