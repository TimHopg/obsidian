---
aliases: libft readme
---
#todo #School42 #C_Language 

#### Boolean etc.
`ft_isalpha()` – is alphabet
`ft_isdigit()` – is number
`ft_isalnum()` – alphanumeric
`ft_isascii()` – is ascii
`ft_isprint()` – is printable character
`ft_isspace()` - is space
`ft_isinset()` - is character part of string
`ft_abs()` - returns absolute value of a long
#### Strings
`ft_strlen()` – length of string

`ft_atoi()` - converts ASCII to int

`ft_memset()` –   sets n number of characters to an unsigned char c
`ft_bzero()` –     zeroes out data
`ft_memcpy()` –   copies n number of bytes from dst to src
`ft_memmove()` – same but deals with overlapping data
`ft_strlcpy()` – copies up to size-1 chars and null terminates
`ft_strlcat()` – concats one string to end of other and null terminates
`ft_toupper()` – converts char to uppercase
`ft_tolower()` – converts char to lowercase
`ft_strchr()` –   finds the first occurrence of char in string
`ft_strrchr()` – finds last occurrence of char in string
`ft_strncmp()` – compares up to n chars in two strings for equivalence
`ft_memchr()` –   finds first occurrence of char in n bytes of memory block
`ft_memcmp()` –   compares first n bytes of two memory blocks for equivalence
`ft_strnstr()` – searches for first occurrence of needle in haystack up to n chars

`ft_strmapi()` – 
`ft_striteri()` – 

`ft_putchar_fd()` –  outputs char to given file descriptor 
`ft_putstr_fd()` –    outputs string to given file descriptor
`ft_putendl_fd()` –  outputs string + new line to file descriptor
`ft_putnbr_fd()` –    outputs integer to given file descriptor
`ft_countwords()` - counts words by separators

#### Malloc Functions
`ft_strdup()` –   allocates memory and duplicates string
`ft_substr()` –   allocates memory and returns substring of string s
`ft_strjoin()` – allocates memory and returns s1 + s2
`ft_strtrim()` – allocates memory and returns copy of s1 with set chars trimmed from beginning and end
`ft_split()` –     returns array of strings from s split by char c
`ft_itoa()` –       allocates memory and returns string of integer
`ft_strndup()` - duplicate string with malloc up to n chars
`ft_calloc()` –   mallocs memory and initiates all to zero