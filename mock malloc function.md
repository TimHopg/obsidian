#C_Language #todo 

```c
#include < unittest/framework.h>  // Replace with your specific framework header

// Mock malloc function
void *mock_malloc(size_t size) {
  static int fail_count = 0; // Counter to simulate overflow on specific call
  if (fail_count++ == 0) {  // Simulate overflow on the first call
    return NULL;
  }
  // Delegate to real malloc for other calls (replace with your actual allocation logic)
  return malloc(size);
}

TEST(ft_calloc_test, overflow_leak) {
  // Replace these with appropriate values for your test
  size_t count = 1000;
  size_t n = 5000;  // This might cause overflow with previous SIZE_MAX check

  // Override malloc with the mock function during the test
  void *(*orig_malloc)(size_t) = malloc;
  malloc = mock_malloc;

  void *ptr = ft_calloc(count, n);

  // Assertions to check for leak (e.g., using a leak detection tool)
  ASSERT_EQ(ptr, NULL);  // Check if ft_calloc returns NULL on overflow

  // Restore the original malloc function
  malloc = orig_malloc;
}

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

TEST(ft_calloc_test, overflow_leak) {
  size_t count = 1000;
  size_t n = 5000;  // This might cause overflow with previous SIZE_MAX check

  // Set a very low virtual memory limit to simulate allocation failure
  rlimit rl;
  rl.rlim_cur = 1024;  // Set a low memory limit (adjust as needed)
  rl.rlim_max = 1024;
  if (setrlimit(RLIM_AS, &rl) == -1) {
    perror("setrlimit");
    return;
  }

  void *ptr = ft_calloc(count, n);

  // Assertions to check for leak (e.g., using a memory leak detection tool)
  ASSERT_EQ(ptr, NULL);  // Check if ft_calloc returns NULL on overflow

  // Reset resource limit (optional)
  rl.rlim_cur = RLIM_INFINITY;  // Reset to default
  setrlimit(RLIM_AS, &rl);
}
```
#### References
[[Malloc]]