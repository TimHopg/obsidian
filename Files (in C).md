#todo #C_Language #Files

`int fd; //file descriptor
`fd = open(filename, O_RDWR | O_CREAT, 0644);
`lseek` - moves fd pointer

`open ("file.txt", O_RDONLY | O_CREAT)`
`|` - bitwise `or` operator which states if the file doesn't exist, create it. Combines flags
#### fopen()
`fopen(filename, mode)`
`w` - write
`a` - append
`r` - read 
`FILE` is a datatype
`FILE *fptr;`  
`fptr = fopen(_filename_, _mode_);`
#### Create File
`w` or `a` - creates file in same location as c file (unless otherwise specified), if it doesn't exist it creates it

```C
FILE *fptr;
fptr = fopen("filename.txt", "w"); // Create a file
fclose(fptr); // Close the file
```

To create a file in a specific place:
`fptr = fopen("C:\directoryname\filename.txt", "w");`
Use `fclose()` to close file after use.
#### Write to File
```C
FILE *fptr;
// Opens file in writing mode
fptr = fopen("filename.txt", "w");
// Writes text to the file. If file already exists, old content is deleted
fprintf(fptr, "Some text");
// Close the file
fclose(fptr);
```
#### Append Content To File
```C
FILE *fptr;    
// Opens file in append mode  
fptr = fopen("filename.txt", "a");  
// Appends text to the file  
fprintf(fptr, "\nHi everybody!");  
// Closes file  
fclose(fptr);
```
#### Read From a File
```C
FILE *fptr;
fptr = fopen("filename.txt", "r"); // Open a file in read mode   
char myString[100]; // Store the content of the file

if(fptr != NULL) // If the file exists
// Reads content and prints. loop because fgets only reads first line
	while(fgets(myString, 100, fptr))
		printf("%s", myString);

else // If the file does not exist 
	printf("Not able to open the file.");

fclose(fptr); // Close the file
```