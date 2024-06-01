#todo #C_Language #Data_Structures 

Arrays are stored contiguously in data.
#### Declaring an Array
`int myNumbers[] = {25, 50, 75, 100};`
OR
`// Declare an array of four integers and add elements later:`
`int myNumbers[4];`
You cannot change the size of the array after creation.
#### 2D Array (vector/matrix)
`int matrix[2][3] = { {1, 4, 2}, {3, 6, 8} };`
`[2]` = rows
`[3]` = columns
```C
int matrix[2][3] = { {1, 4, 2}, {3, 6, 8} };  
  
int i, j;  
for (i = 0; i < 2; i++) {  
  for (j = 0; j < 3; j++) {  
    printf("%d\n", matrix[i][j]);  
  }  
}
```
#### References
[[Data Structures]]

_2024-05-27 15:32_
