---
aliases: chmod
---
#Shell 

`chmod` changes access permissions
`chmod a-w filename`

##### Use binary
`chmod 751 filename` = 111 101 001 = rwx r-x --x

`a` - all
`w` - write
`-` - remove
`+` - add

Users > Groups > Other
`d` - directory
`r` - read
`w` - write
`x` - executable
`drwx--xr-x`
`--w-r-x-wx`