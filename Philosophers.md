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
#### Atomic operations
When one philosopher asks for the lock, another philosopher cannot ask at the same time – to avoid a lock being granted to two philosophers simultaneously.
#### Compilation
link with `cc -pthread main.c` pthread flag
#### Creating a Thread
`#include <pthread.h>

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
`pthread_join` - blocks the execution of a thread until another thread finishes.
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

#### References
[CodeQuoi](https://www.codequoi.com/en/)

_2024-08-17 17:49_