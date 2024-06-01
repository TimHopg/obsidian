#Shell #C_Language #Programming 

`cc -Wall -Wextra -Werror -c *.c && ar rcs libft.a *.o

`-c` compiles all c files, stopping before the linking phase, creating .o output fies
`ar` = archive 
`rcs` = replace create index

`cc -Wall -Wextra -Werror -c *.c && ar rcs libft.a *.o 

`cc` - standard compiler
`Wall` - all warning messages
`Wextra` - extra warning messages
`Werror` - treats warning messages as errors
`-c` - doesn't link files into an executable
`&&` runs if previous command was successful
`ar` - archive
`rcs` - replace/create (s = symbol table)
then filename
`*.o` - using all output files