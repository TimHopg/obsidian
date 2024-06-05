#todo #C_Language #Programming 

Used to perform operations at the bit level.

_AND_ (`&`) - compares each bit of first operand to each bit of second. If both bits are `1` the resulting bit is set to `1`, otherwise it's set to `0`.
- can be used as a test to compare user permissions against required permissions
	- `110 & 111 = 110` - only the permissions a user has are returned 

_OR_ (`|`) - if either bit (or both) is `1`, the result is set to `1`, otherwise, `0`.
- can be used to combine multiple permissions
	- `100 | 010 = 110` - e.g. read permissions + write permissions

_XOR_ (`^`) - _exclusive or_ - if bits are different, the result is `1`, otherwise, `0`.
- can be used to remove permission from existing set
	- `101 ^ 001 = 100` - removes execute permission

_NOT_ (`~`) - is used on a single number and inverts the digits

_Left Shift_ (`<<`) - Shifts the bits to the left by the number specified. Vacated bits on the right are filled with `0`'s.
- a left shift of 1 effectively doubles a number

_Right Shift_ (`>>`) - Shifts bits to the right by number specified.
	e.g. `5 >> 1` = `0101 >> 1` = `0010`
- a right shift of 1 halves a number

_NAND_ (`~(A & B)`) - achieved using combination of _NOT_ and _AND_.
#### Print Binary from Decimal

```C
unsigned char octet = 5;
unisgned char bit;
int i = 8;
while (i--) {
  bit = (octet >> i & 1) + '0';
  write(1, &bit, 1); }
```

`i` is set to 8 to allow us to print the 8 digits. (the loop runs from 7 -> 0)
our octet is 5 -> `0000 0101`
Loop 1: `i = 7`: `0000 0101` is shifted 7 bits to the right.
	`& 1` - masks all bits but the LSB because `1` = `0000 0001` so when combined with the AND operator, everything is set to zero except the LSB if it's a `1`.
This would then print `1` or `0` depending on the LSB.
#### Signed Binary
The first bit of an 8 bit number represents the sign.
`0000 0000` - positive
`1000 0000` - negative
With negative binary numbers, the remaining 7 digits is counting up from 128.

_LSB_ - _Least Significant Bit_ - The rightmost bit, lowest in value
#### The Relationship Between Binary and Hex
A single hex digit is the equivalent of a nibble (4 bits) `1111` = `F`.
When printing a binary number in C `0b11110000` an octet. This can be printed as `%02X` using `printf()`. It says to pad with leading `0`'s and make it `2` characters long.
#### Swap Bytes without Additional Variable (using _XOR_)
`a = 1001`
`b = 1010`
`a = a XOR b = 0011`
`b = a XOR b = 1001`
`a = a XOR b = 1010`

Use _XOR_ three times and the values have swapped.
#### References
[[Twos Complement]]
[[Binary]]

_2024-06-02 10:05_