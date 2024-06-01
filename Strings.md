#C_Language 

```c
char *str;
str = "LOL";
str = str + 1; // points to one memory allocation to the right. POINTER ARITHMETIC

/* str now is equal to "OL" */

if (str != '\0')
{
    DO SOMETHING
}
```

the pointer points to the address of the first character and it continues reading until it hits a null character.

```c
char *str; // string literal
char str[] = " "; // string as array
```