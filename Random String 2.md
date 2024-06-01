#Random #C_Language #Testing 

```c
char random_char(int index) {
char charset[] = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
return charset[index];
}

srand(time(NULL));
char str[17];
int i, index;for (i = 0; i < 16; i++) {
   index = rand() % 62;
   str[i] = random_char(index);
}
str[i] = '\0'; // Terminate string
```