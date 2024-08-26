#todo #C_Language 

An enum (enumeration) is a group of constants. The first item has the value 0 as default then 1, 2, etc..

If you change the value of the first, the following items update accordingly. Or you can assign values to each

```C
enum Level {
	LOW,
	MEDIUM,
	HIGH
	};
```
#### Using enums in a Switch Statement
```C
enum Level {  
  LOW = 1,
  MEDIUM,
  HIGH
};  
  
int main() {  
  enum Level myVar = MEDIUM;
  
  switch (myVar) {
    case 1:
      printf("Low Level");
      break;
    case 2:
      printf("Medium level"); 
      break;
    case 3:
      printf("High level");
      break;
  }
  return 0;
}
```

#### References
[[C Language Tips]]
[[Programming Tips]]


_2024-06-20 22:21_