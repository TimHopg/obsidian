#todo #School42 #Programming #C_Language 

## Parsing

thinking...
What if we 

We need something like `strtok()`.
 [recursive descent parser](http://en.wikipedia.org/wiki/Recursive_descent_parser)
https://www.cs.unc.edu/~porter/courses/comp530/f23/lab1.html
https://github.com/rehassachdeva/C-Shell/blob/master/parse.c
https://stackoverflow.com/questions/10112038/parsing-commands-shell-like-in-c



### Double Quotes

Allow for variable expansion and command substitution but prevent word splitting and interpretation of special characters (except `$`, and `\`). We only need to worry about `$` (an env variable) in minishell.  
  
Without a space before the quotes, the shell interprets the word before and after the quotes as one token.  
  
E.g. `echo abc"def"` outputs `abcdef`, any spaces inside the quotes would also be preserved.  
  
`set -- abc"def"; echo $#` outputs `1`  
`set -- abc "def"; echo $#` outputs `2`  
  
`set --` reassigns positional parameters `$1 $2` etc. to each token.  
`echo $#` prints the number of assigned positional parameters i.e. tokens  
  
`set -- abc "def ghi"; echo $#` outputs `2`  
  
### Single Quotes  

Single quotes prevent all special character interpretation.  
    
## Functions


`readline(char *prompt)`  
  
Requires `-lreadline` flag to compile.  
`prompt` displays as a prompt.  
Returns the line entered on the terminal. This is mallocated and must be freed by the user.  
If `EOF` is encountered while reading the line and the line is empty `NULL` is returned.
#### References
[FrankenShell Doc](https://github.com/AshParker19/42_minishell/blob/main/docs/documentation.md)
https://github.com/AshParker19/42_minishell/blob/main/docs/documentation.md
https://minishell.org/echo__builtin_8c.html

_2024-08-04 19:31_