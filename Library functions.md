---
aliases: libft readme
---
#School42 #C_Language 
#### Boolean etc.
`ft_isalpha()` – is alphabet?
`ft_isdigit()` – is number?
`ft_isalnum()` – alphanumeric?
`ft_isascii()` – is ascii?
`ft_isprint()` – is printable character?
`ft_isspace()` - is space char?
`ft_isascii()` - is ascii char?
`ft_isinset()` - is character part of string?
`ft_abs()` -         returns absolute value of a long
`ft_toupper()`–  converts char to uppercase
`ft_tolower()` – converts char to lowercase
`ft_atoi()` -        converts ASCII to int
#### Memory
`ft_memset()` –   sets n number of characters to an unsigned char c
`ft_bzero()` –     zeroes out data
`ft_memcpy()` –   copies n number of bytes from dst to src
`ft_memmove()` – same but deals with overlapping data
`ft_memchr()` –   finds first occurrence of char in n bytes of memory block
`ft_memcmp()` –   compares first n bytes of two memory blocks for equivalence
#### Output
`ft_putchar_fd()` – outputs char to given file descriptor 
`ft_putstr_fd()` –   outputs string to given file descriptor
`ft_putendl_fd()` – outputs string + new line to file descriptor
`ft_putnbr_fd()` –   outputs integer to given file descriptor
`ft_putbase_fd()` -  outputs and int in a given base to file descriptor
#### Lists
`ft_lstadd_back()` -   appends node to list
`ft_lstadd_front()` - prepends node to list
`ft_lstclear()` -         frees each node in list and sets pointer to `NULL`
`ft_lstdelone()` -       frees contents of single node using function pointer
`ft_lstiter()` -           iterates through list and applies function `f` to each node
`ft_lstlast()` -           returns last node of list
`ft_lstmap()` -             iterates through list applying function `f` to each node and returns new list
`ft_lstnew()` -             mallocs new node
`ft_lstsize()` -           returns size of list
#### Strings
`ft_strlen()` –   returns length of string (minus terminating character)
`ft_strlcpy()` – copies up to size-1 chars and null terminates
`ft_strlcat()` – concats one string to end of other and null terminates
`ft_strchr()` –   finds the first occurrence of char in string
`ft_strrchr()` – finds last occurrence of char in string
`ft_strncmp()` – compares up to n chars in two strings for equivalence
`ft_strnstr()` – searches for first occurrence of needle in haystack up to n chars
`ft_countwords()` - counts words by separators
`ft_striteri()` – Applies function `f` to each character of string in place
#### Malloc Functions
`ft_strdup()` –   allocates memory and duplicates string
`ft_substr()` –   allocates memory and returns substring of string s (from `start` to length `l`)
`ft_strjoin()` – allocates memory and returns s1 + s2
`ft_strtrim()` – allocates memory and returns copy of s1 with set chars trimmed from beginning and end
`ft_split()` –     returns array of strings from s split by char c
`ft_itoa()` –       allocates memory and returns string of integer
`ft_strndup()` - duplicate string with malloc up to n chars
`ft_calloc()` –   mallocs memory and initiates all to zero
`ft_strmapi()` – applies function `f` to each character of string and returns malloc'd string
#### Other
`ft_printf()` -         own implementation of `printf()`
`get_next_line()` - returns malloc'd next line from file descriptor
