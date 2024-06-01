#C_Language 

String Duplicate 
`#include <string.h>

The  strdup() function returns a pointer to a new string which is a duplicate of the string s.  Memory for the new string  is  obtained  with malloc(3), and can be freed with free(3).

On  success,  the strdup() function returns a pointer to the duplicated string.  It returns NULL if insufficient memory was available, with errno set to indicate the cause of the error.