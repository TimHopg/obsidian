#todo #Shell #Programming #C_Language 

When forking, the order of operations is not guaranteed. We use wait to produce results in the order we determine and to make sure a program doesn't end before all processes have finished.

```C
if (id != 0) // if main process
	wait(NULL)
```

The above code is redundant because `wait`() waits for child process to finish.
You need only `wait(NULL)`. __HOWEVER__ it only waits for one child to finish so be careful with multiple forks:

```C#
#include <errno.h>
while (wait(NULL) != -1 || errno != ECHILD)
```

`errno != ECHILD` - states that the error returned is not due to having no children (it's due to something else). 

Wait returns `-1` if it produces an error i.e. there are no child processes to wait for.
It returns the PID of the process that was waited for.

Wait blocks the calling process until one of its child processes exits or a signal is received. If a child process has already exited, it returns immediately.


#### References
[[Pipex]] [[fork]]

_2024-05-25 12:11_