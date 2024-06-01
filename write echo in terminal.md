#C_Language 

```c
#include <unistd.h>

void	write_in_term(void)
{
	char	c;

	while (read(STDIN_FILENO, &c, 1) > 0)
		write(1, &c, 1);
}
```

STDIN_FILENO is a macro defined in unistd.h that represents the file descriptor for the standard input stream (the keyboard typically).