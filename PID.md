#todo #Programming #C_Language 

Every process has an ID. A number unique to that process.

`#include <sys/wait.h>`
[[getpid]]() - returns a `pid_t` (int) and doesn't take any parameters
[[getppid]]() - returns the process's parent ID

If the parent process terminates before the child has had a chance to, a new parent id will be assigned to the child, it will be a zombie process. It is important to _wait for child processes to finish_ so you don't have memory leaks:
`wait(NULL)` - only need this and not the code below because [[wait]] waits for child processes to finish.

```C
if (id != 0)
	wait(NULL);
```
#### References
[[Pipex]] [[wait]] [[fork]]

_2024-05-25 14:13_