#todo 
#### Typecasting
`float x = (float) 5 / 2`
#### Constants
`const float PI = 3.1415` - consts are read only usually declared in capitals
#### Function Points
[[Function Pointers]] can be type cast to improve readability
#### Break and Continue
`break` exits the loop.
`continue` breaks one iteration (in the loop) if a specified condition occurs

All numbers 0 - 10 will be printed except 4:
```C
int i;  
  
for (i = 0; i < 10; i++) {
  if (i == 4) {
    continue; }  
  printf("%d\n", i);  
}
```
#### For Loop
```C
for (initializationStatement; testExpression; updateStatement) {
	code block to be executed_  
}
```
#### Do While
#### Ternary Operators
```C
// If x > 10, add 17 to y. Otherwise add 37 to y.
y += x > 10? 17: 37;

// Prints "odd" if odd, "even" if even
printf("The number %d is %s.\n", x, x % 2 == 0? "even": "odd");
```
#### Switch Statements
#### Compiling Standards
`gcc -std=C89` - forces compile using the C89 standard. (add `-pedantic`)
#### Comma Operator
The value of the comma expression equates to the value of the right-most expression:
`x = (1, 2, 3) // x = 3`
#### size_t
`sizeof()` is determined at compile time not at run-time
`%zu` - positive _size_t_ values
`%zd` - negative _size_t_ values
#### References
[[Pre & Post Decrement Increment]]
[[Bitwise Operators]]
[[Code Structure]]

_2024-05-27 15:04_