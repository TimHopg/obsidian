#C_Language 

`n--` Post decrement operator. returns current value of n then decrements.
`--n` Pre-decrement character. Reduces the value of n by one then decrements

```C
i = 10;  
j = 5 + i++; // Compute 5 + i, _then_ increment i
printf("%d, %d\n", i, j); // Prints 11, 15

i = 10;  
j = 5 + ++i; // Increment i, _then_ compute 5 + i
printf("%d, %d\n", i, j); // Prints 11, 16
```