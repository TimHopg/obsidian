#School42 #C_Language 

* compile with the following flags  
`-D BUFFER_SIZE=n  
`cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 <files>.c  
  
* handle binary files  
  
Does your function still work if the BUFFER_SIZE value is 9999? If it is 1? 10000000? Do you know why?  
  
Try to read as little as possible each time get_next_line() is  
called. If you encounter a new line, you have to return the current line.  
Don’t read the whole file and then process each line.  
  
You are not allowed to use your libft in this project.  
• lseek() is forbidden.  
• Global variables are forbidden  
  
  
When writing your tests, remember that:  
1) Both the buffer size and the line size can be of very different  
values.  
2) A file descriptor does not only point to regular files.  
Be smart and cross-check with your peers. Prepare a full set of  
diverse tests for defense.