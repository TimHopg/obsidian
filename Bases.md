#Maths 
##### Recursion
Divide number (n) by the base (b) until n < b then reassemble.

```c

blen = base length
	
if (nbr < 0)
	{
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

[one base to another [YouTube]](https://youtu.be/hIs3A6gGz2w?si=8_fPH_qtNwnX3EeL)
[decimal to any base [YouTube]](https://www.youtube.com/watch?v=szkJP9bSr3k&ab_channel=bparanj)