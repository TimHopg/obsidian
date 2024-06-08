#Makefile #School42 #Programming 

Makefiles are whitespace sensitive

`CFLAGS = -Wall -Wextra -Werror -I../include` - warning flags and `-I` include flag which specifies the folder where header files will be stored

`target: dependencies
``	action

`OBJS = $(SRCS:.c=.o)
`OBJS are all SRCS but with .o instead of .c
`CUR_DIR = $(shell pwd)
`-C change directory

`@` suppresses output to command line

`CFLAGS` is a keyword so it is handled implicitly

`make -n` executes make showing all commands

`$<` first dependency
`$^` all dependencies
`$@` target

#### References
[[Code Structure]]