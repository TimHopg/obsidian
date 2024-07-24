#todo #C_Language #Shell 

`#include <unistd,.h>`

`fork()` splits the execution line.
A child process is born and executes alongside the parent process (at the same time).
`fork()` - returns a process ID. The child process is always going to be zero.
	This can be used to distinguish between child and parent/main processes.
	`if pid == 0` etc. `else`

The number of processes is 2^n where n = no. of forks

Should check if `pid == 0` and only fork if it's not ie we're on the main process:
```C#
if (id != 0)
	fork();
```

If you are forking during your program, you should use [[wait]]() at the end of the program to ensure your child processes have a chance to finish and aren't left orphaned.

If two forks are created, the hierarchy will look as follows
[[Child Processes 1.canvas|Child Processes]]
#### References
[[Pipex]] [[PID]] [[wait]] [[pipe]]

_2024-05-25 11:38_