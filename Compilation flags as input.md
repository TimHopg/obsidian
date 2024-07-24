#C_Language 

Define keywords to accept flags during compilation.

```js
#ifndef BUFFER_SIZE  
#define BUFFER_SIZE 512 // Default value  
#endif
```

`gcc -D BUFFER_SIZE=1024 your_program.c -o your_program`
`-D` - defines a macro

[[Argc Argv 1]] takes in arguments on the command line.
#### References
[[Preprocessor]]