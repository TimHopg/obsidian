#Memory #Programming #todo

Checks memory leaks
`valgrind ./a.out

Compile with `-g` flag for additional debugging info (line numbers etc.)
Also add `-O0` optimisation zero to ensure no information is optimised away during compile
`valgrind --leak-check=full --show-leak-kinds=all -s ./a.out

Use [[Leaks on Mac]]