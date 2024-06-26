#Maths #C_Language #todo 

A number that can only be divided by 1 and itself.
`2, 3, 5, 7, 11...`
1 is not a prime because it can only be divided by one number.

A prime is a `nbr` where no `n` exists that `nbr % n = 0` (where `n < nbr` and `n > 1`).
Every `n` between `1` and `nbr` where `nbr % n` will produce a result other than zero.

```C
if nbr <= 1 // not prime
  return 0;

if nbr == 2 // prime
  return 1;

//if nbr % 2 == 0 -> not prime
i = 3;
while (i <= nbr / i) // i sq. == nbr if nbr is not prime so no need to check beyond nbr / i
{
  if (nbr % i == 0) // not prime
    return 0;
  i += 2;
}
return 1;
```
#### References
[fastest way to check if number is prime](https://www.rookieslab.com/posts/fastest-way-to-check-if-a-number-is-prime-or-not)

_2024-06-04 21:34_