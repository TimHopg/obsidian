#todo #Programming 
Mac's version of GDB.
`lldb` then `help`

*the flag `-0` in the compiler messes with lldb*

`lldb ./program.out` - enters LLDB
`gui` - launches GUI
`run` - runs program
`target create progname` - sets target as executable
`b main` - sets breakpoint at main
*`breakpoint set --name main`* <- this works
`s` - step into
`n` - next
`ni` - next instruction (assembly)
`bt` - backtrace
#### References
[[GDB Debugging]]

_2024-05-24 22:04_
