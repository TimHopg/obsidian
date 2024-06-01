#Memory #Programming #todo

Checks memory leaks
`valgrind ./a.out

Compile with `-g` flag for additional debugging info (line numbers etc.)
`valgrind --leak-check=full --show-leak-kinds=all -s ./a.out

Use [[Leaks on Mac]]