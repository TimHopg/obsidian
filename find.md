#Shell 

```shell
find . -type f \( -name '*~' -o -name '## \) -exec rm {} \;
```

`find .` - current directory
`-type f` - files only
`\(` - escape character for parenthesis
`-name '*~'` - all files ending in tilde
`-o`
`'##` starting or ending in pound
`-exec rm` - execute remove

find by default works recursively

`find . -type f -o -type d | wc -l`
`-type d` - directories
`|` - pipe - output of one command serves as the input of the next
`wc -1` - word count

#### References
[[Fzf]]