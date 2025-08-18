# Literal 
This page will show you how different types of literals are represented in Cambo 
programming language.  
A literal is basically a textual representation of a value of a data type written 
directly in the source code.
For example:
- `12` is an integer literal
- `"hello, world"` is a string literal

**Note: The notation below might have some syntax errors.**

| Type                          | Notation                             | Example                            |
| :---------------------------- | :----------------------------------- | :--------------------------------- |
| Decimal integer               | [+-]?[0-9]+                          | `11`, `+12`, `-13`, `01s`          |
| Octal integer                 | [+-]?0[oOcC][0-7]+                   | `0o22`, `+0o20`, `-0c02`           |
| Hexadecimal integer           | [+-]?0[xX][0-9a-zA-F]+               | `0x33`, `+0xff`, `-0x0f`           |
| Binary integer                | [+-]?0[bB][01]*                      | `0b01`, `+0b1101`, `-0b111`        |
| Fractional floating-point     | [+-]?[0-9]*.[0-9]+                   | `0.1`, `.1`, `1.0`, `+1.2`, `-1.2` |
| Exponential floating-point    | [+-]?[0-9]+[eE][+-]?[0-9]+           | `2e10`, `2e+3`, `3e-4`, `+4e-3`    |
| Fractional with Exponetial FP | [+-]?[0-9]*.[0-9]+([eE][+-]?[0-9]+)+ | `2.5e-3`, `-3.14e+10`, `+4.5e2`    |
| Imaginary number              | [+-]?([0-9]+(\.[0-9]+)?)?i           | `i`, `+2i`, `-3.2i`                |
| Character                     | '([^'\\] \| \.)'                     | `'A'`, `'B'`, `'@'`, `'\n'`        |
| String                        | "([^"\\] \| \.)"                     | `"hello"`, `"hi!\n"`, `"world\t"`  |
| Boolean                       | true or false                        | `true`, `false`                    |
| Null                          | null                                 | `null`                             |

TODO: Add more literal types.