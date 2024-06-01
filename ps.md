---
aliases: lsof
---
#Shell 

`ps` - Process status, displays active processes
`lsof` - List open files

`ps`
```shell
PID TTY           TIME CMD
 6607 ttys000    0:00.78 -zsh
 6619 ttys000    0:00.00 -zsh
 6659 ttys000    0:00.00 -zsh
 6661 ttys000    0:00.01 -zsh
 ```
 `lsof -p 6607` -p specifies process