#todo #School42 #Programming #C_Language 

## Parsing

thinking...

We need to write a _grammar_ that describes the priority of each expression. This will be represented by a tree that the parser will traverse. 

`strtok()` is a `ft_split()` to tokenise strings.
 [recursive descent parser](http://en.wikipedia.org/wiki/Recursive_descent_parser) 
https://www.cs.unc.edu/~porter/courses/comp53./f23/lab1.html  
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

### `readline()`

`readline(char *prompt)`  
  
Requires `-lreadline` flag to compile.  
`prompt` displays as a prompt.  
Returns the line entered on the terminal. This is mallocated and must be freed by the user.  
If `EOF` is encountered while reading the line and the line is empty `NULL` is returned.

https://web.mit.edu/gnu/doc/html/rlman_2.html
https://tiswww.case.edu/php/chet/readline/readline.html#index-rl_005fon_005fnew_005fline

#### `rl_clear_history()`

Clears `readline`'s private history list.

#### `rl_on_newline()`

Call this before redisplaying the input prompt, esp in cases where the previous line might not have ended in a newline (e.g. when a partial command is given or the line editing gets interrupted (`SIGINT`)).

#### `rl_redisplay()`

Redisplays the prompt.
#### `rl_replace_line()`

`int rl_replace_line(const char *text, int clear_undo);.  
`text` is a pointer to the string that will replace the current line.

#### `add_history()`

`void add_history(const char *line);.  
`readline()` doesn't automatically store every input, you have to manually call `add_history()` to store it. Allows you to skip non-meaningful lines.
#### References
[FrankenShell Doc](https://github.com/AshParker19/42_minishell/blob/main/docs/documentation.md)
https://github.com/AshParker19/42_minishell/blob/main/docs/documentation.md
https://minishell.org/echo__builtin_8c.html

_2024-08-04 19:31_