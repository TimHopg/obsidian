#Memory #C_Language 

Leaks is a [[Valgrind]] Mac equivalent

`-g symbols identify error lines

`gcc -g -Wall -Wextra -Werror filename.c
`leaks --atExit --list -- ./programname

`MallocStackLogging=1