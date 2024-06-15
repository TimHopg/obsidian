#C_Language 

A function pointer is just as the name suggests. A pointer to a function. A function that is saved as a variable.

Any functions with the same prototypes can be sent as a function pointer.
```C
int add(int a, int b) {return a + b}; // simple functions
int mult(int a, int b) {return a * b};

int do_operation(int (*operation)(int, int), int x, int y)
{ return operation(x,y); } 

int main(void) {
  int result = do_operation(add, 5, 4);
  int result2 = do_operation(mult, 5, 4);
}
```

Function pointers can also be `typedef`'d:
`typedef int ft_operation(int, int);`
then declared as:
`ft_operation *op;`

Declare a function pointer within a function:
`void (*function)(int a, int b);`
Then in your code, if something... `function = func_add;`.

Function pointers are defined at run time, not at compile time so their dependencies can be updated.
#### References


_2024-05-31 18:44_