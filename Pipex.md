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
#### File Descriptors
In Unix-like operating systems, everything is a file, including standard input (stdin), standard output (stdout), and standard error (stderr). Understanding file descriptors and how they're used for I/O operations is crucial.
#### Forking Processes
The fork() system call is used to create a new process. You'll need to understand how to create child processes and how they inherit file descriptors from the parent process.

Executing Commands: Use exec() family of functions (like execl(), execv(), etc.) to execute commands in the child process. This involves loading a new program into the current process space.

Piping: Pipes are used to connect the output of one process to the input of another. You'll need to understand how to create a pipe using the pipe() system call, how to redirect standard input and output using dup2(), and how to close file descriptors appropriately.

Parent-Child Communication: After forking, the parent and child processes communicate through the pipe. You'll need to understand how to write data into the pipe from one process and read it from another.

Error Handling: Proper error handling is essential in systems programming. Learn how to check for errors returned by system calls and handle them appropriately.

Signal Handling: While not directly related to pipes, signal handling is important for robustness. You may need to handle signals such as SIGPIPE to gracefully handle situations where a pipe is broken.

Concurrency and Synchronization: If you plan to work with multiple pipes or multiple processes, you'll need to understand concepts like race conditions and synchronization mechanisms (e.g., mutexes, semaphores) to ensure proper coordination between processes.

Memory Management: Understand memory allocation and deallocation, especially if you're dynamically allocating memory for buffers or data structures related to your pipe implementation.

Testing and Debugging: Finally, learn techniques for testing your code thoroughly and debugging any issues that arise. Techniques like using printf statements, strace, valgrind, or gdb can be immensely helpful.

Start with basic examples of forking processes and using pipes, then gradually build up your understanding and implementation. Don't hesitate to consult the Unix manual pages (man) and online resources for further guidance. Good luck with your project!

The additional requirements you mentioned do add some complexity to your project, but the core concepts remain the same. Here's how you might adjust your approach:

Parsing Command-Line Arguments: You'll need to parse the command-line arguments to identify the input file, output file, commands, and any redirection operators (<<, >>). This may involve using libraries like getopt() or manually parsing the arguments.

Redirection Operators: Handle redirection operators (<<, >>) by opening and closing files appropriately. For <<, you'll need to read from the file until a specified delimiter is encountered. For >>, you'll need to append output to the file instead of overwriting it.

Handling Multiple Pipes: Extend your implementation to handle multiple pipes by creating additional pipes and forking processes as needed. Each command in the pipeline will have its own input and output redirected appropriately.

Error Handling and Edge Cases: Be sure to handle errors and edge cases robustly. This includes checking for the existence of files, permissions, handling cases where commands or files are missing, etc.

Testing: Test your program thoroughly with various input scenarios, including different combinations of commands, files, and redirection operators. Automated testing can be particularly useful here to ensure your program behaves correctly in various scenarios.

Code Organization: As your program becomes more complex, consider organizing your code into separate functions or modules to improve readability and maintainability.

Documentation: Document your code thoroughly, especially if you're working on a team or if others might need to understand or extend your code in the future.

While these additional requirements do add complexity, they build upon the fundamental concepts of inter-process communication, file I/O, and process management. By breaking down the problem into smaller tasks and gradually implementing and testing each component, you can build a robust and functional implementation of the pipex command.
#### Here Document (heredoc)

#### References
* [[fork]]
* [[PID]]
* [[wait]]
* [[pipe]]

_2024-07-19 12:53_