#todo #School42 

A project about threads.

The problem is...
There is a table of philosophers who can each eat, sleep or think.
In order to eat they must take the fork from the left and the right of them (therefore making it impossible for their neighbours to eat at the same time).
Once a philosopher has finished eating, they sleep. When they're awake they start thinking.
There is no communication between philosophers (so they don't know when another is about to die).

* Each philosopher is a thread
* Each fork is a mutex

This problem was dreamt up by Dijkstra to illustrate the problems that can arise in a computer system where two processes try to access the same block of memory at the same time.

You can introduce a kind of monitor into the system that allows each philosopher to ask permission to take the forks and thus eat but if they are unable to get both forks, they will replace any forks they have so other philosophers can try. This is known as a lock. You can combine a lock with some kind of hierarchy of who is hungriest.
### Atomic operations
When one philosopher asks for the lock, another philosopher cannot ask at the same time – to avoid a lock being granted to two philosophers simultaneously.
### Threads
Threads are basic units of CPU utilisation. We can have multithreaded processes to make use of more of the CPU's capacity.

Threads share:
* *code*
* *data*
* *files*

But have their own:
* *registers*
* *stack*

Multithreaded programs can continue running even if part of the program is blocked or performing a lengthy operation.
It also benefits from resource sharing to keep programs small.
### Race Conditions
Occur when two threads' operations interfere with each other.  
`var++;` includes a read, increment and write to memory call. if another thread tries to write before another thread has completed the whole operation, the output might be unexpected.  
`gcc -S main.c` - compiles in assembly to see what the processes are doing
### Compilation
link with `cc -pthread main.c` pthread flag
#### Creating a Thread
`#include <pthread.h>` – POSIX thread library

```c
int pthread_create(pthread_t *restrict thread, 
					const pthread_attr_t *restrict attr,
					void *(*start_routine)(void *),
					void *restrict arg);
```
`thread` - a pointer to `pthread_t` type
`attr` - allows default attributes to be changed (normally `NULL` here will suffice)
`start_routine` - a pointer to a function that takes a `void *arg` and returns `void *`. This is the function where the thread will start its execution.
`arg` - a pointer to an argument to pass `start_routine` arguments. To pass several arguments, this pointer should be a data_structure.
#### Joining/Detaching Threads
`pthread_join` - blocks the execution of a thread until another thread finishes. It is called join because the thread is rejoining the main thread.

```c
int pthread_join(pthread_t thread, void **retval);
```

`thread` is the ID of the thread that this thread should wait for.
`retval` contains the return value but `NULL` is enough here.
This returns `0` for success or an error code for a failure.

Unlike processes, we have to specify the ID of the thread to wait for. We cannot simply wait for the next child to finish.

We can, however, tell the OS to reclaim resources from a thread as soon as it finishes executing (without the need to wait). This is known as detaching.

```c
int pthread_detach(pthread_t thread);
```
### Data Races
A data race occurs when two threads try to access the same block of memory at the same time.

`gcc -fsanitize=thread -g threads.c && ./a.out`

Fsanitize thread shows this.
### Mutex
Short for Mutual Exclusion is a lock that allows us to regulate data access and prevent data races. 
#### Declaring Mutexes
`pthread_mutex_t mutex;`

```c
int pthread_mutex_init(pthread_mutex_t *mutex,
					   const pthread_mutexattr_t *mutexattr);
```

We can leave the second argument as `NULL`.
#### Locking/Unlocking a Mutex
```c
int pthread_mutex_lock(pthread_mutex_t *mutex));
int pthread_mutex_unlock(pthread_mutex_t *mutex);
```
If the mutex is unlocked, `lock` locks it and the calling thread becomes its owner, the function ends immediately. If the mutex is already locked by another thread, `lock` suspends the execution of the calling thread until the mutex is unlocked.

`unlock` unlocks the mutex but doesn't check if the thread calling it is its owner. If it's not, we may get lock order violation errors.
#### Destroying a Mutex
`pthread_mutex_destroy(mutex);`

Destroys an unlocked mutex and frees any resources it's holding but only if it's unlocked. Attempting to destroy a locked mutex results in undefined behaviour.
### Deadlocks
When mutexes cause each thread to wait for one another, this is called a deadlock and the program must be killed.
### Testing Programs with Threads
Test multiple times when using threads because some lucky synchronisation can occur.

Use:
* `-fsanitize=thread -g`
* `valgrind --tool=helgrind ./prog_name <args>`
* `valgrind --tool=drd ./prog_name <args>`
* `-fsanitize=address` & `valgrind`
* compiling with `-S` stops the compiler after assembly code has been created but before creating an object
#### References
[CodeQuoi](https://www.codequoi.com/en/)
[Oceano Medium: Philo](https://medium.com/@jalal92/the-dining-philosophers-7157cc05315)
[Oceano Medium: Deadlocks](https://medium.com/@jalal92/deadlocks-b059eed3e6c3)
[Oceano Medium: Threads](https://medium.com/@jalal92/lets-discuss-threads-grab-a-coffee-ad4d4ebf7181)
[Youtube: Jamshidbek](https://www.youtube.com/watch?v=UGQsvVKwe90)
[Medium: MannBell](https://m4nnb3ll.medium.com/the-dining-philoshophers-an-introduction-to-multitasking-a-42-the-network-project-34e4141dbc49)
[Medium: Dean Ruina](https://medium.com/@ruinadd/philosophers-42-guide-the-dining-philosophers-problem-893a24bc0fe2)
[Youtube: CodeVault Threads Playlist](https://www.youtube.com/watch?v=d9s_d28yJq0&list=PLfqABt5AS4FmuQf70psXrsMLEDQXNkLq2&pp=iAQB)

_2024-08-17 17:49_