#Maths 
##### Recursion
Divide number (n) by the base (b) until n < b then reassemble.

```c

blen = base length
	
if (nbr < 0) {
		// output[0] = '-';
		i = 0;
	}
	if (nbr == 0)
		return (0);
	if (nbr != 0)
	{
		ft_dtob(nbr / blen, base);
		// printf("%c", base[nbr % blen]);
		output[i++] = base[nbr % blen];
```

```C
// returns 0 - 9 if c is '0' - '9' and 10 + for 'A' to 'F'
int val(char c) {
  if (c >= '0' && c <= '9')
    return (int)c - '0';
  else
    return (int)c - 'A' + 10;
}

// Convert nbr from base 'b' to decimal

int toDeci(char *str, int base)
{
  int len = `strlen``(str);`

    `int` `power = 1;` `// Initialize power of base`

    `int` `num = 0;`  `// Initialize result`

    `int` `i;`

    `// Decimal equivalent is str[len-1]*1 +`

    `// str[len-2]*base + str[len-3]*(base^2) + ...`

    `for` `(i = len - 1; i >= 0; i--)`

    `{`

        `// A digit in input number must be`

        `// less than number's base`

        `if` `(val(str[i]) >= base)`

        `{`

           `printf``(``"Invalid Number"``);`

           `return` `-1;`

        `}`

        `num += val(str[i]) * power;`

        `power = power * base;`

    `}`

    `return` `num;`

`}`

`// Driver code`

`int` `main()`

`{`

    `char` `str[] =` `"11A"``;`

    `int` `base = 16;`

    `printf``(``"Decimal equivalent of %s in base %d is "`

           `" %d\n"``, str, base, toDeci(str, base));`

    `return` `0;`

`}`
```

[one base to another [YouTube]](https://youtu.be/hIs3A6gGz2w?si=8_fPH_qtNwnX3EeL)
[decimal to any base [YouTube]](https://www.youtube.com/watch?v=szkJP9bSr3k&ab_channel=bparanj)