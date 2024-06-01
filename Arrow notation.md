#C_Language 

```c
struct s_group
{
	int a;
	char c1;
};

struct s_group my_group;
struct s_group *sp;

sp = &my_group;
(*sp).c1 = 48; // == sp->c1 = 48;
```

