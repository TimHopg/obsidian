#Maths 

### Two's complement rule
Invert the bits (1's complement) and then add 1.
##### Hex
MSB 0 - 7 -> positive
MSB 8 - F -> negative

To compute the two’s complement of a n-digit hexadecimal numeral, either:

* complement each digit (exchange 0 for F, 1 for E, and so on) and then add one to the whole numeral
* subtract the numeral from (In hexadecimal) one followed by n zeroes.

If the number is not a whole number of hexadecimal digits, some adjustments to the above must be made for the first digit:

* For the first method, complement the first digit using the appropriate number of bits. For example, with 22 bits, the first hexadecimal digit uses only two bits, so exchange 0 for 3, 1 for 2, 2 for 1, and 3 for 0.
* For the second method, subtract from the appropriate power of two. For example, for 22 bits, subtract from (hexadecimal) 400000.
##### Notes
If the carry in and carry out to the sign bit (MSB) are different, then it's a sure sign of overflow. 