---
aliases: fork
---
#todo #Shell #C_Language #Programming 

Requires `#include <unistd.h>`
Takes in an array of two integers. Two file descriptors. _0 is read and 1 is write_

Fork splits the process into two.  `0` is the new process (the child process) and the process id of the new process to the old process. So the non-zero PID will be the main or the previous process.

All processes have an id => PID.

```C#
#include <unistd.h>

int main(int argc, char **argv)
{
	int fd[2]; // fd[0] = read, fd[1] = write
	if (pipe(fd) < 0) {
		return 1;}
	int id = fork();
	if (id == 0) { // writing block
		close(fd[0]); // can close read because we are in child process
		TAKES IN INPUT (int x (scanf or something));
		write(fd[1], &x, sizeof(int));
		close(fd[1]);}
	else {
		close(fd[1]);
		int y;
		read(fd[0], &y, sizeof(int))
		close(fd[0])};
}
```

Recommended to check `pipe()` is equal to `0` ie is successful or `-1`, fails.
`fd`'s are inherited from one process to another so it's important to `pipe()` before `fork`ing.
#### Fork and Pipe
```C
int main(int argc, char **argv)
{
  int arr[] = {1, 2, 1, 2};
  int arr_size = sizeof(arr) / sizeof(int); // gives no. of ints
  int start, end;
  int fd[2];
  if (pipe(fd) == -1) {
    return 1;}
  int id = fork();
  if (id == -1) {
    return 2;}
  if (id == 0) { // child
    start = 0;
    end = (start +  )arr_size / 2;
  } else { // parent
    start = arr_size / 2;
    end = arr_size;
    }

  int sum = 0;
  int i;
  for (i = start; i < end; i++) {
    sum += arr[i]; }

  printf("Calculated partial sum: %d\n", sum);

  if (id == 0) { // writes from child to parent
    close(fd[0]);
    write(fd[1], &sum, sizeof(sum));
    close(fd[1]); }
  else { // reads from parent to child
    int sum_child;
    close(fd[1]);
    read(fd[0], &sum_child, sizeof(sum_child));
    close(fd[0]); }

  int total_sum = sum + sum_child;
  printf("Total sum is %d\n", total_sum);
  wait(NULL);
}
```
#### References
[[Pipex]] [[wait]] [[fork]]

_2024-05-25 19:08_