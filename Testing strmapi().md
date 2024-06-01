#School42 

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include "libft.h"

char test_function(unsigned int i, char c)
{
    if (i % 2 == 0)
        return (c + 1);
    else
        return (c - 1);
}

void test_ft_strmapi(char const *test_name, char const *input, char const *expected_output)
{
    char *result = ft_strmapi(input, test_function);

    if (strcmp(result, expected_output) == 0)
    {
        printf("%s: PASS\n", test_name);
    }
    else
    {
        printf("%s: FAIL\n", test_name);
        printf("Expected: \"%s\"\n", expected_output);
        printf("Got:      \"%s\"\n", result);
    }

    free(result);
}

int main(void)
{
    // Test cases
    test_ft_strmapi("Test 1", "hello", "ifmmp");
    test_ft_strmapi("Test 2", "", "");
    test_ft_strmapi("Test 3", "12345", "02468");
    test_ft_strmapi("Test 4", "aBcDeF", "bAdFcE");

    return (0);
}
```