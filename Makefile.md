#Makefile #School42 #Programming 

`target: dependencies
``	action

`$<` first dependency
`$^` all dependencies
`$@` target - when you see this essentially copy and paste the target to where it is

`%.o: %.c` - (`%` wildcard) any `.o` file depends on the same `.c` name file

`CFLAGS = -Wall -Wextra -Werror -Iinclude` - warning flags and `-I` include flag which specifies the folder where header files will be stored (Redacted: `../include` - one directory up, relative to `SRC` files)

`OBJS = $(SRCS:.c=.o)` - OBJS are all SRCS but with .o instead of .c
`CUR_DIR = $(shell pwd)`
`-C` change directory

`@` suppresses output to command line

`CFLAGS` is a keyword so it is handled implicitly

Makefiles are whitespace sensitive
`make -n` executes make showing all commands



#### References
[[Code Structure]]