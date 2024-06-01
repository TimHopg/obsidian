### User limits
`ulimit -a` - lists soft limits of all processes
`ulimit -a -H` - lists hard limits of all processes

#### See
`getrlimit` and `setrlimit` in `C`
`FOPEN_MAX` - minimum number of guaranteed streams that can be opened
`sysconf(_SC_OPEN_MAX)` system wide limits