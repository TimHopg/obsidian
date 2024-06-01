#C_Language 

`#include <stdlib.h>`
Use `sizeof()` to allocate the correct number of bytes
`malloc(sizeof(int) * 3)

Malloc takes a number of bytes as a number `(malloc(4))`, allocates those bytes
on the heap and return a pointer to those bytes

If you ever want to try to allocate more memory than available, malloc returns `NULL`
#### Free
When done using memory, use `free(ptr);` and assign ptr to null, `ptr == null;`
__C Standard explicitly states__ that nothing occurs if you attempt to free a `NULL` pointer.


`if (arr == NULL)
 ``   exit(1); // if not in main (else return 1)

### Force NULL return
#### Option 1
`#define malloc(...) NULL`
Predetermines malloc behaviour to always return NULL. Checks if you're code is handling failed malloc attempts correctly

#### Option 2
``` C#
#define malloc(size) my_malloc(size, __FILE__, __LINE__)

void *my_malloc(size_t size, const char *file, int line)
{
	static int fail_next_allocation = 0;
	
	if (fail_next_allocation)
	{
		fail_next_allocation = 0;
		fprintf(stderr, "Forced memory allocation failure at %s:%d\n", file, line);
		return NULL;
	}
	else
	{
		return malloc(size);
	}
}
```

Include define and function and set `fail_next_allocation` to `1` at any point in the code.
Then check Valgrind for leaks.