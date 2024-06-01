#Random #C_Language #Testing 

```c
// A C++ Program to generate test cases for
// random number
#includebits/stdch
using namespace std;
 
// Define the number of runs for the test data
// generated
#define RUN 5
 
// Define the range of the test data generated
#define MAX 10000000
 
int main()
{
    // Uncomment the below line to store
    // the test data in a file
    // freopen("Test_Cases.in", "w", stdout);
 
    // For random values every time
    srand(time(NULL));
 
    for (int i=1; i<=RUN; i++)
        printf("%d\n", rand() % MAX);
 
    // Uncomment the below line to store
    // the test data in a file
    //fclose(stdout);
    return(0);
}
```