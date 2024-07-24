#todo #C_Language #Programming 

#### Laws
- Avoid deep nesting
	- Try inverting logic. Instead of `if is` try `if not` or vice versa
	- Merge related if statements
- Extraction
	- Extract complex logic to its own methods or functions
- Avoid Duplication
	- Extract code duplication into its own function or variable
- Follow Naming Convention

Comments can be less necessary if the code is written well.
Eliminate the need for comments by naming correctly, using constants/macros instead of magic numbers etc.
- Code is updated, comments are often not
#### Declaring Function Convention
`rtn function(arg);` // function statement before main()
`function(arg);` // call function in main

// function definition below main()
`rtn function(void) {`
	`functioin code }`
#### Organise Project

```
project/
├── src/
│   ├── main.c
│   ├── file1.c
│   └── file2.c
├── include/
│   └── push_swap.h
└── Makefile
```

###### Flags
`cc -Wall -Wextra -Werror -Iinclude src/*.c -o prog_name`
`-Iinclude` - includes header files found in include folder
`src/*.c` - wildcard include all c files in src
`-o` - output name
`-L libft -lft` - Library folder and library name `-l` = lib and `ft` = end of libft (minus the lib).

The project's `.h` file can `#include` the `libft.h` file. When the `.o` files are being compiled, the `libft.a` library need not be linked until the binary is being created.

So `Iinclude` during the `.o` creation and `-L libft -lft` during the linking phase.
#### References
[[Makefile 1]]
[[C Language Tips 1]]

_2024-06-08 13:55_