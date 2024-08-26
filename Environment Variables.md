---
aliases: envp
---
#todo #C_Language #Programming 

Environment variables are inherited from the parent process. A C program's parent is the shell which is where it inherits the env variables from.

`export ENV_VARIABLE= test` - exports the variable to the environment so they can be used.
*OR* `ENV_VARIABLE=test ./main` - makes the variable available to be used only by the program and not exported to the shell.

`char * env_variable = getenv("ENV_VARIABLE");`

Can be added to `.env` file or bash profile etc.
`envp` is `NULL` terminated so can be iterated over.

`int main(int ac, char **av, char **envp)`

#### References
[[C Language Tips]]
[[Programming Tips]]


_2024-07-27 16:29_