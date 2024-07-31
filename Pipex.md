#School42 #todo 
#### Redirects and Pipes
`<` - input redirect. sends a file descriptor to `stdin (fd0)` which can then be received by a command.
`>` - output redirect. sends `stdout (fd1)` of a command to a file.
these both always goes between fd (or file) and a command but can be written `< infile cmd1` which is a bit confusing.
(`>>`) - append output redirect
`2>` sends to `stderr (fd2)`

`command > output.txt 2>&1` - redirects output of standard out and standard error to same file. 

`< file grep a1` = `grep a1 < file`
`|` - pipe redirects output of one command to the input of the next command
Pipes connect processes and redirects connect processes with files or file descriptors.

`cmd1 < input.txt | cmd2 > output.txt`
Separate the commands by the pipe and work out what each side is doing. `input.txt` is being sent to the input of `cmd1` which is then being piped to the input of `cmd2` and `cmd2`'s output is being sent to `output.txt`.
#### Here Document (heredoc)
Allows the user to specify multiline input directly on the command line or script. Everything until the delimiter is inputed as text (usually EOF).
```SHELL
cat << EOF
line 1
line 2
EOF
```
Works like input redirect `<` but allows user to type the text themselves
### access()
`int access(constant char *pathname, int mode)`

`access()` checks whether the program can access `pathname`.
`mode` determines which checks are performed.
* `F_OK` checks for file existence
The following check for existence plus:
* `R_OK` - read permissions
* `W_OK` - write permissions
* `X_OK` - execute permissions
They can be separate by bitwise or operators.
`access()` returns `0` if successful or `-1` if an error occurred. `errno` is set.
### dup2()
`int dup2(int oldfd, int newfd);`

`dup2()` makes `newfd` a copy of `oldfd`, closing `newfd` first if necessary.
* If `oldfd` is not a valid fd, the call fails and `newfd` is *NOT* closed
* If `oldfd` is valid and `newfd` has the same value, `dup2()` does nothing and returns `newfd`.
They now can be used interchangeably and share the same offset and file status flags. Any changes made to one will affect the other.

So if you pass `STDOUT_FILENO`(standard out file number) as `newfd` you can reroute another file descriptor to the standard out.
*`dup2()` doesn't just move a file descriptor, it creates another one so you must close the previous `fd` after calling it*
### pipe()
`int pipe(int pipefd[2]);`

`pipe()` creates a unidirectional data channel that can be used for interprocess communication. The array `pipefd` returns two file descriptors referring to the ends of the pipe. `pipefd[0]` is the read end of the pipe and `pipefd[1]` is the write end of the pipe. Data written to the write end of the pipe is buffered by the kernel until it is read from the read end of the pipe

On success, `0` is returned. On error, `-1` is returned, and `errno` is set appropriately.
### fork()
`pid_t fork(void);`

`fork()` creates a new process by duplicating the calling process. The new process, referred to as the `child`, is an exact duplicate of the calling process, referred to as the `parent`, except for in the following [cases](https://linux.die.net/man/2/fork)
### waitpid()
`pid_t waitpid(pid_t pid, int *status, int options);`

The `waitpid()` system call suspends execution of the calling process until a child specified by _pid_ argument has changed state. By default, `waitpid()` waits only for terminated children.
``` C
int pid;
pid = fork();
waitpid(pid);
```
### wait()
`pid_t wait(int *status);`

The `wait()` system call suspends execution of the calling process until one of its children terminates.
```C
// waiting for multiple children
int main(void){
	int status;

    while (n > 0)
    {
        wait(&status);
        n--;
    }}
```
### execve()
`int execve(const char *filename, char *const argv[], char *const envp[]);`

`execve()` executes the program pointed to by `filename`. This is the path of the program like `ping`. Could be `usr/bin/ping`.

`argv` argument is `{"program_name", "flag/argument1", "flag/argument2", NULL}`
The argv string must be NULL terminated.

`execve()` does not return on success, the calling process is **replaced** by the executed `filename` but the PID remains the same.
The whole process is replaced by the program so nothing can be run in this process afterwards. Anything afterwards will only be run if an error occurs with `execve()`.

`envp` will be the environment variables that the new process will have access to. You can send a modified `envp` list to give it access to a specific library path for instance.

For error handling, you can use the same process without conditionals since any code after `execve()` will not run if `execve()` is successful.
### unlink()
`int unlink(const char *pathname);`

`unlink()` deletes a pathname from the file system. If that name was the last link to a file and no processes have the file open the file is deleted and the space it was using is made available for reuse.

If the name was the last link to a file but any processes still have the file open the file will remain in existence until the last file descriptor referring to it is closed.

On success, `0` is returned. On error, `-1` is returned, and `errno` is set appropriately.
#### File Descriptors
In Unix-like operating systems, everything is a file, including standard input (stdin), standard output (stdout), and standard error (stderr). Understanding file descriptors and how they're used for I/O operations is crucial.
#### Forking Processes
The fork() system call is used to create a new process. You'll need to understand how to create child processes and how they inherit file descriptors from the parent process.
#### Executing Commands
Use `exec()` family of functions (like `execl()`, `execv()`, etc.) to execute commands in the child process. This involves loading a new program into the current process space.
#### Piping
Pipes are used to connect the output of one process to the input of another. You'll need to understand how to create a pipe using the `pipe()` system call, how to redirect standard input and output using `dup2()`, and how to close file descriptors appropriately.
#### Parent-Child Communication
After forking, the parent and child processes communicate through the pipe. You'll need to understand how to write data into the pipe from one process and read it from another.
#### Error Handling
Proper error handling is essential in systems programming. Learn how to check for errors returned by system calls and handle them appropriately.
#### Signal Handling
While not directly related to pipes, signal handling is important for robustness. You may need to handle signals such as SIGPIPE to gracefully handle situations where a pipe is broken.
#### Concurrency and Synchronization
If you plan to work with multiple pipes or multiple processes, you'll need to understand concepts like race conditions and synchronization mechanisms (e.g., mutexes, semaphores) to ensure proper coordination between processes.
#### Memory Management
Understand memory allocation and deallocation, especially if you're dynamically allocating memory for buffers or data structures related to your pipe implementation.
#### Testing and Debugging
Finally, learn techniques for testing your code thoroughly and debugging any issues that arise. Techniques like using printf statements, strace, valgrind, or gdb can be immensely helpful.
#### Error Handling and Edge Cases
Checking for the existence of files, permissions, handling cases where commands or files are missing, etc. Test with different combinations of commands, files, and redirection operators. Automated testing can be particularly useful here to ensure your program behaves correctly in various scenarios.
## Project
To avoid zombie/orphan processes, it's important for all parent processes to `wait()` until the child processes have terminated.
When using multiple forks, processes may have more than one child process. So `wait(NULL)` by itself may not work correctly. Instead use:
```C
while (wait(NULL) != -1 && errno != ECHILD)
	(void)0;
```

`dup2(fd[1], STDOUT_FILENO)` - reroutes the standard out to file descriptor 1 which is the write end of the pipe. `fd[0]` = read, `fd[1]` = write.

It's looking like we will need a fork for each process ie a fork for each `cmd`.
	forks = number of `cmd`'s
And a pipe to go between number of commands only. dup2 will take care of reading from infile and to outfile so no pipes are needed there. (Is that the case with here_doc), we will see.
	pipes = `cmd`'s - 1

You need get_next_line for here_doc.
#### > Redirect
When file does not exist, it is created but also truncated. 
``
#### SIGPIPE
`yes | head -n 5` - The `yes` command continuously outputs "yes" until it is killed. After head has read its 5 lines it closes the input stream. The next time `yes` tries to write it instead receives a `SIGPIPE` signal which is how it knows when to terminate.
#### References
* [[fork]]
* [[PID]]
* [[wait]]
* [wait & waitpid](https://linux.die.net/man/2/wait)
* [[pipe]]
* [access()](https://linux.die.net/man/2/access)
* [[dup2()]]
* [dup2()](https://linux.die.net/man/2/dup2)
* [unlink](https://linux.die.net/man/2/unlink)
* CodeVault processes playlist YouTube

_2024-07-19 12:53_