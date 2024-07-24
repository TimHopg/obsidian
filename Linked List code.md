#Data_Structures #Algorithms 

```c
typedef struct node // needs to be defined as node so the ptr works
{
    int number;
    struct node *next; // wouldn't work without struct node def
} node;

node *list = NULL; // initiate an empty linked list so it doesn't point to garbage value

node *n = malloc(sizeof(node)); // creates ptr and struct (data and ptr)

n -> number = 1; // is same as (*n).number = 1
n -> next = NULL;
```

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct node
{
    int number;
    struct node *next;
} node;

int main(int a, char *av[])
{
    node *list = NULL;

    for (int i = 1; i < argc; i++)
    {
         int number = atoi(argv[i]);
         node *n = malloc(sizeof(node));
         if (n == NULL)
             return 1; // AND free memory
         
         n -> number = number; // put number variable at where ptr points
         n -> next = list; // prepend node to list
         list = n; // set list to node created
    }

    // Print list
    node *ptr = list; // create a pointer that points to the list itself
    while (ptr != NULL) // while it doesn't point at the last field
    {
        printf("%i\n", ptr -> number);
        ptr = ptr->next; // set the ptr to the next node
    }
}
```

#### References
[[Linked Lists]]