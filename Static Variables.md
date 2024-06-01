#C_Language 

Stored on the data segment (not the heap or the stack)  
  
Retain their value through multiple calls.  
Numeric types are initialized to zero.  
Pointer types are initialized to NULL.  
  
`static int staticVar = 0;  
because it is set to zero only during declaration it won't be reinitialised to zero on each call. it will retain its value.