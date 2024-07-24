#todo #bash 

Powerful text processing tool

`awk '$1 == "word"...` -  if first field matches "word"...
`...{print $3}'` - print what's in the 3rd field

`variable ~ /pattern/` tilde tests if a string matches a REGEX

`END` - END block carries out an action after everything else has happened. like a summing operation to print the total
`{}` - action pairs. carries out what's in the braces if the first pattern is true
`awk '$1 == "foo" { print }' input.txt > output.txt` - if 1st field is equal to foo it will print the entire line, read from input.txt to output.txt
#### References
[[Regex]]

_2024-05-15 21:48_