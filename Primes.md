#Maths 

`if nbr % n = 0 (where n < nbr and n > 1)

`if nbr <= 1
	`ret 0

`if nbr == 2 -> prime
`if nbr <= 1 -> not prime
`if nbr % 2 == 0 -> not prime
`while i < nbr/2
`if nbr % i == 0 -> not prime
`i++;

[fastest way to check if number is prime](https://www.rookieslab.com/posts/fastest-way-to-check-if-a-number-is-prime-or-not)