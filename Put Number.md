#todo #C_Language
#### Recursive
```C
void ft_putnbr(int n) {
  if (n >= 10)
    ft_putnbr(n / 10);
  char c = (n % 10) + '0';
  write(1, &c, 1);
}
```

If number is more than 1 digit, divide by ten and feed it back into the function.
Once it's 9 or less, `n % 10` to find the remainder (add `'0'` to convert to char) and write.
The recursion will `write` the last operation (`/ 10`) first so largest digit will be written first and the number will be printed in the correct order.
#### References


_2024-06-04 21:05_