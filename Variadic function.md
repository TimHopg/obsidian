#C_Language 

A function that can take a variable number of arguments e.g. printf()

```c
#include <stdarg.h>

va_list ap/args;
va_start(ap, num); // num is number of arguments;
va_arg(ap, int); // pass va_list var and var type
// each time va_arg is called, it cycles to the next arg
va_end(ap);
```

passing `va_list` by value to other functions results in undefined behavior so should be passed as reference (ptr)
### va_list
* Is a structure/array that is used by `va_start` `va_arg` `va_end`.
* Stores additional elements that are used in variadic functions.

`va_list ap; // can define ap (argument pointer) without * because va_list is already defined as type pointer
### va_start
* takes two arguments: (`va_list`, `last_known_parameter`)
* initialises argument_list for use by `va_arg` and `va_end`. `va_start` must be called first.
* last_known_parameter is the name of the last parameter of the calling function
eg.
`int ft_printf(const char *format, ...) // format is the last known parameter
### va_arg
* takes `va_list` and type of arg (argument_type)
* Each time it is called it modifies the `argument_list` so that the following argument will be returned next time
### va_end
* close with `va_end`

#### References
[[]]