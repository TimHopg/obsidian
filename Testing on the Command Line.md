#todo #C_Language #Testing #Shell

```C#
#include <fcntl.h>
#include <stdio.h>

int main(int argc, char **argv)
{
	int fd;
	char *line;
	
	(void)argc;
	fd = open(argv[1], O_RDONLY);
	while ((line = get_next_line(fd)) != NULL)
	{
		printf("%s", line);
		free(line);
	}
	close(fd);
}
```

`./a.out > output.txt` - to direct output to text file

#### References
[[Argc Argv 1]]