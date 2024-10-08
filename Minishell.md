#todo #School42 #Programming #C_Language 

## Ideas/Style guide
- Set all unused `fd`s to `-1` when not in use or being used.
- Use `safe_free()` to free memory.
- Leave a comment by each variable that is mallocated so we can safely free all allocated memory.
## Parsing

thinking...

We need to write a _grammar_ that describes the priority of each expression. This will be represented by a tree that the parser will traverse. 

An example for orders of operations:

```C
expr -> term + expr | term
term -> factor * term | factor
factor -> (expr) | int
```

An expr can be a term + an expression or a term
A term can be a factor * term or a factor
A factor can be an (expr) or an int

Pseudocode for parsing an expression (line 1 above):  
First deal with the case if it is a term + expr. Parse a term, if it succeeds call it `x`.
Then parse a char `+`.
Then parse an expression and call it `y`.
return `x + y`.
OR the expression could just be a term.

Pseudocode for parsing a term is almost the same as for an expression.

Pseudocode for parsing a factor:  
Can be a bracketed expression or an integer.
First parse char `(`.
Parse expression and call it `x`.
Parse a char `)`
return `x`.
Or parse an integer.

This allows us to both parse and evaluate the expression as we go.

The only thing missing are the definitions for parsing each type.
Parsers will consume a string and then return a result plus anything not consumed. If it can't pass anything, it returns an empty string.

`strtok()` is a `ft_split()` to tokenise strings.  
 [recursive descent parser](http://en.wikipedia.org/wiki/Recursive_descent_parser) 
https://www.cs.unc.edu/~porter/courses/comp53./f23/lab1.html  
https://github.com/rehassachdeva/C-Shell/blob/master/parse.c  
https://stackoverflow.com/questions/10112038/parsing-commands-shell-like-in-c  
https://en.wikipedia.org/wiki/Backus%E2%80%93Naur_form  
### Hierarchy

Shells have a natural hierarchy, pipelines redirections etc. Each node can represent a command and each child nodes can represent components, arguments, files for redirection, subcommands.

Recursive descent parser has a function for each type of grammar rule, commands, operators, arguments etc. This makes it easier to extend the shell with more complex features.

< file cmd1
cmd1 < file

file1 cmd1 cmd2 file2

cmd1 < file1  &&  cmd2 > file2

### High-level Design

- Split the string into tokens (commands, operators (`|`, `&&`, `>` etc.))
- Define grammar rules for shell syntax
- Write parsing functions that correspond to each grammar rule.
	- `parse_command()`
	- `parse_pipeline()`
	- `parse_expression()` - `&&` `||`
- Abstract Syntax Tree
	- Leaf nodes are individual commands
	- Internal nodes are operators (e.g. `&&`)
- To execute traverse the tree to execute commands
	- For a pipeline, traverse each command node in the order they need to be executed, chaining outputs
	- For logical operations, evaluate the left and right child nodes based on the operator (e.g. `&&` only evaluates the right side if the left succeeds).

For an input like:  
`cmd1 | cmd2 && cmd3 > output.txt`

Your parser could produce an AST that looks like:  
```
		   &&  
		 /    \
	   |        >
	  / \      / \
  cmd1 cmd2 cmd3 output.txt
```

- The `|` node means `cmd1` pipes into `cmd2`.
- The `&&` node means `cmd3` runs only if the pipeline `cmd1 | cmd2` succeeds.
- The `>` node means `cmd3` redirects its output to `output.txt`.

#### Grammar for Example Language

`::=` is defined as

```BNF
<sentence> ::= <subj> <verb> <obj>
    <subj> ::= <art> <noun> | the robot
	 <art> ::= the | a
	<noun> ::= dog | cat| man | woman | robot
	<verb> ::= bit | kicked | stroked
	 <obj> ::= <art> <noun> | two furry dice   ; "two furry dice is a globbet that isn't parsed"
```

Each symbol on the left (`<sentence>`) has a stack of prerequisites on the right. So it will search for a `<subj>` then a `<verb>` and finally an `<obj>`.  
Once `<subj>` has been satisfied, it is popped off the top of the stack.

_When parsing `<subj>`, we see that it could be `<art>` and `<noun>` so those will be added to the top of the stack and popped when they are satisfied._

Sentence: _"The robot stroked two furry dice"_

We will use the top-down approach i.e. don't look for leaf nodes in the tree and try and work your way up. Instead always start at the top (the root) of the tree and work your way down to see if a sentence can be parsed (decoded).
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

## Implementation

### Grammar

`::=` - is defined as
`<symbol>`
`[foo]` - `foo` is optional
`^` - not
`*` - zero or more
`+` - one or more

`<compound_command>` is run separately to other commands. In the shell any changes compound commands make to environment variables do not affect the other commands (which are run in the parent shell). The subject only mentions priority so subshells I think are beyond the scope of the project.

```CFG
# Top-level structure
; command line input is defined as command_sequence or compound_command
<command_line> ::= <command_sequence> | <compound_command>

<command_sequence> ::= <pipeline> | <command_sequence> "&&" <pipeline> |<command_sequence> "||" <pipeline>

<compound_command> ::= "(" <command_sequence> ")"

# Pipeline
<pipeline> ::= <command> | <pipeline> "|" <command>

# Command structure
<command> ::= <simple_command> [<redirections>]

<simple_command> ::= <command_prefix> [<command_word>] [<command_suffix>] | <command_word> [<command_suffix>]

<command_prefix> ::= <io_redirect> | <command_prefix> <io_redirect>

<command_suffix> ::= <io_redirect> | <word> | <command_suffix> <io_redirect> | <command_suffix> <word>

<command_word> ::= <word>

# Word and quoting
<word> ::= <unquoted_word> | <single_quoted_content> | <double_quoted_content>

<unquoted_word> ::= <char>+ | "$" <env_var_name>

; single_quoted_content starts and ends with single quotes and contains anything else inside. optional ([]) any character (*) not (^) single quote (')
<single_quoted_content> ::= "'" [^']* "'"

<double_quoted_content> ::= '"' (<char> | "$" <env_var_name> | <whitespace>)* '"'

; environment variables must have one or more alphanumeric chars (or underscore)
<env_var_name> ::= [a-zA-Z0-9_]+

<char> ::= any printable character except whitespace and metacharacters

# Redirections
<redirections> ::= <io_redirect> | <redirections> <io_redirect>

<io_redirect> ::= <input_redirect> | <output_redirect> | <heredoc>

<input_redirect> ::= "<" <word>

<output_redirect> ::= ">" <word> | ">>" <word>

<heredoc> ::= "<<" <word>

# Additional rules
<whitespace> ::= [ \t]+
; do we need a newline rule?
```
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