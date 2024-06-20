#todo #C_Language #Files

`int fd; //file descriptor
`fd = open(filename, O_RDWR | O_CREAT, 0644);
`lseek` - moves fd pointer

`open ("file.txt", O_RDONLY | O_CREAT)`
`|` - bitwise `or` operator which states if the file doesn't exist, create it. Combines flags
#### fopen()
`fopen(filename, mode)`
`w` - write
`a` - append
`r` - read 
`FILE` is a datatype
`FILE *fptr;`  
`fptr = fopen(_filename_, _mode_);`
###