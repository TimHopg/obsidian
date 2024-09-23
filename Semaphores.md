#todo #C_Language #Programming 

Semaphores are atomic, they occur uninterrupted i.e. cannot be accessed concurrently. And are an alternative to *mutexes*.

Semaphores can be set to any value.
If you *wait* for a semaphore it decreases it's value by `1` if possible. If the value is already `0`, the process will pause until it is able to continue.
When you *post* to a semaphore, you increase its value by `1`.

#### References
[[Philosophers]]

_2024-09-06 16:11_