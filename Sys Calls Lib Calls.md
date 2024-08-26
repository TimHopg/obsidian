---
aliases: Library Calls, strace
---
#todo #C_Language #Programming 

System calls make a request to the kernel (ring 0)
Library calls might make use of system calls but not necessarily.

`strace ./prog_name` will show a list of all the system calls used by a program 
`ltrace ./prog_name` - shows library calls
#### References


_2024-08-02 17:16_