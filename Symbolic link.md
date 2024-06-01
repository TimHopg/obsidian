---
aliases: ln
---
`ln -s test0 test6` -  creates a symbolic or soft link of `test0` called `test6`

Symbolic links point to a path so moving the original directory/file will leave the link dangling. 
`ln -sf new/path/etc. link` - Force update the path to the link.

A hard link points to the data, like a pointer. It basically creates another directory entry for the same memory inode.
`ln file1 link1` - omit the -s#todo 

#### References
[[Shell Commands]]

_2024-05-13 22:51_