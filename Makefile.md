#Makefile #School42 #Programming 

`target: dependencies
``	action

Once `dependencies` are satisfied/created, the `target` can be run by doing the `action`

`$<` first dependency
`$^` all dependencies
`$@` target - when you see this essentially copy and paste the target to where it is

`%.o: %.c` - (`%` wildcard) any `.o` file depends on the same `.c` name file

`CFLAGS = -Wall -Wextra -Werror -Iinclude` - warning flags and `-I` include flag which specifies the folder where header files will be stored (Redacted: `../include` - one directory up, relative to `SRC` files)

`OBJS = $(SRCS:.c=.o)` - OBJS are all SRCS but with .o instead of .c
`CUR_DIR = $(shell pwd)`
`-C` change directory

```makefile
$(OBJ_DIR)%.o: $(SRC_DIR)%.c
	@mkdir -p $(OBJ_DIR)
	@$(CC) $(CFLAGS) -c $< -o $@ $(INCLUDE)
```

`mkdir -p` - creates intermediate directories as required
`@` suppresses output to command line

_Note:_ Always link your external libs AFTER your object files! Not doing so may lead to an `undefined reference`.

`CFLAGS` is a keyword so it is handled implicitly

Makefiles are whitespace sensitive
`make -n` executes make showing all commands

If your first rule is `all:` that will run if you type just `make`

`-` - dash before a command says run and continue running even if error occurs
#### Add Rules For Other tasks
- `diff: git diff --stat` - to show git diffs before commiting
- tarballs
- other git tasks

#### Developing on both platforms

`ifeq uname` is Linux set some variables to something. Else set them to something else.

``` makefile
ifeq ($(shell uname), Linux)
	MLX_INCLUDE = -I/usr/include -Imlx
	MLX_FLAGS = -Lmlx -lmlx -L/usr/lib/X11 -lXext -lX11
else # OSX
	MLX_INCLUDE = -I/opt/X11/include -Imlx
	MLX_FLAGS = -Lmlx -lmlx -L/usr/X11/lib -lXext -lX11 -framework OpenGL -framework AppKit
endif
```

#### References
[[Code Structure]]