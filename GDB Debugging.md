#todo #Programming 
### GNU Debugging
Compile with `-g` flag
`gdb ./a.out` - to enter debugging in gdb
`lay next` - layout next
`break main` - adds breakpoint at main
`run` - runs program until breakpoint
`next` - jumps to next line in c code (`nexti` is next line instruction (assembly))
`step` - steps into (doesn't stay in main but steps into current function) (`next` can be used to step over that function)
`ref` - refresh to tidy up screen

- `ulimit -c unlimited` - sets core files limit to unlimited
- `cat /proc/sys/kernel/core_pattern` - prints where core files are being saved
- `echo "./core > /proc/sys/kernel/core_pattern` - will save core dumped files to current directory
- include `-g` symbols for debugging when compiling
- `gdb ./program_that_crashes ./core_dump` - include offending program and core dump

#### References
[[LLDB]] is mac equivalent
[[Debugging in VS Code]]

_2024-05-24 19:45_