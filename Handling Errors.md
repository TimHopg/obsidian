---
aliases: perror, strerror, errno
---
#todo #C_Language #Programming 

`#include <stdio.h>` - for perror()
`#include <errno.h>` - for errno
`#include <string.h>` - for strerror()

errno is a global variable that is set when a lot of standard library functions fail to give you more verbose error messages. Many functions use errno so if you don't use what it returns straight away, make sure it is saved to a variable.

`strerror(errno)` - interprets `errno` as a useful string.
`perror("prepend")` shortens this process by print the current `errno` to the `stderr`.
#### Macro for error checking
Get Claude's help on this. Macros can print the filename and line number when they're called
```
#define CHECK(X) ({int __val = (X); (__val ==-1 ? \
		({fprintf(stderr, "ERROR ("__FILE__": %d) --
		%s\n",__LINE__,strerror(errno)); \
		exit(-1);-1;}) : __val); }) I
```
#### References
[[C Language Tips]]
[[Programming Tips]]

_2024-07-21 18:33_