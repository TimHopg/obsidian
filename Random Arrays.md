#Random #C_Language #Testing 

```c
// A C++ Program to generate test cases for
// array filled with random numbers
#includebits/stdch
using namespace std;
 
// Define the number of runs for the test data
// generated
#define RUN 5
 
// Define the range of the test data generated
#define MAX 10000000
 
// Define the maximum number of array elements
#define MAXNUM 100
 
int main()
{
    // Uncomment the below line to store
    // the test data in a file
    //freopen ("Test_Cases_Random_Array.in", "w", stdout);
 
    //For random values every time
    srand(time(NULL));
 
    for (int i=1; i<=RUN; i++)
    {
        // Number of array elements
        int NUM = 1 + rand() % MAXNUM;
 
        // First print the number of array elements
        printf("%d\n", NUM);
 
        // Then print the array elements separated 
        // by space
        for (int j=1; j<=NUM; j++)
            printf("%d ", rand() % MAX);
 
        printf("\n");
    }
 
    // Uncomment the below line to store
    // the test data in a file
    //fclose(stdout);
    return(0);
}
```
