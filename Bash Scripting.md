#Shell #todo 

`#!` - the purpose of the shebang is to tell the operating system which interpreter to use

`#!/usr/bin/env bash` - an improved shebang that uses the command env to locate the bash path. it doesn't assume where bash is installed. good for portability
`#!/usr/bin/bash` - the more common shebang 

`;` - separates commands (like new line)
`&&` - run second command only if first is successful
`&` - runs second process even before first has finished
`|` - pipe sends output from one command to input of the next. fewer pipes are better for efficiency
`ifthis && echo "yes" || echo "no"` - && if true and || 'or' if not
### Examples
#### Print each filename
``` bash
for f in ./files/*; do (glob operator, does not require external tools (ls))
	echo "file is $f" // quotes (good practise)
done

// 1 liner
for f in ./files/* ; do echo "files is $f" ; done
```
instead of:
```
for f in `ls folder_name` ; do // ls lists on one line, will treat space as new file. backticks for other operations
	echo file is $f // poor practice (no quotes)
done // will print file names with spaces as separate

// 1 liner
for f in `ls folder_name` ; do echo file is $f ; done
```
#### Loop over arguments
```shell
for arg in "$@" ; do // @ == array.each
	echo "<$arg>"
done

// 1 liner
for arg in "$@" ; do echo "<$arg>" ; done
```
#### References
[[Shell Commands]]

_2024-05-13 22:52_