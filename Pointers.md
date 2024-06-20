#C_Language 

`int *ptr; // naming convention

a pointer is an address in memory

`*ptr` is the value that lives at the address
`*` = dereferencing operator (dereference)

`&a` = address of a
`&` = referencing operator. gives address of value (reference)

### Declaring Pointers
```c
int (ptr_name *)(int, int);
ptr_name = function_name;

int res;
res = ptr_name(5, 10);

// or pass ptr = &func;
//then res = (*ptr_name)(5, 10);
```