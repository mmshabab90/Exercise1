# Reasons for concurrency and parallelism


To complete this exercise you will have to use git. Create one or several commits that adds answers to the following questions and push it to your groups repository to complete the task.

When answering the questions, remember to use all the resources at your disposal. Asking the internet isn't a form of "cheating", it's a way of learning.

 ### What is concurrency? What is parallelism? What's the difference?

-Concurrency, is the ability for a program to be decomposed into parts that can run independently of each other. This means that tasks can be executed out of order and the result would still be the same as if they are executed in order.

-Parallelism refers to techniques to make programs faster by performing several computations in parallel. This requires hardware with multiple processing units. In many cases the sub-computations are of the same structure, but this is not necessary.

-The different lies in order. For concurrent tasks, the order does not matter and the end result will turn out the same anyways. For parallell tasks, the order is important to preserve the results.
 
 ### Why have machines become increasingly multicore in the past decade?

-We can't increase the core clock speed due to heat output and stuff, so we have to innovate in other ways to increase performance such as having multiple cores in the CPU. This allows us to run concurrent processes at the same time.
 
 ### What kinds of problems motivates the need for concurrent execution?
 (Or phrased differently: What problems do concurrency help in solving?)

-Concurrent execution is necessary to utilize multithreaded processors full performance.
 
 ### Does creating concurrent programs make the programmer's life easier? Harder? Maybe both?
 (Come back to this after you have worked on part 4 of this exercise)

-If the program can be split into independent parts that does not have to communcate between eachother, concurrent programming should make the programmer's life easier.

-When the independent parts have to communicate, synchronization could be different to manage, thus making the programmer's life harder.
 
 ### What are the differences between processes, threads, green threads, and coroutines?
 
-A process describes the running program as a whole.

-A thread is a sub-program. Splitting processes into threads allows it run and complete a less time consuming thread before returning to the previous thread.

-A green thread is a thread that is not scheduled by the OS, but by it's own software schheduler. This allows for simulating multi threaded operation in an OS that does not necessarily natively support threading.

-Coroutines is manual threading it has multiple points for suspending and resuming execution. Thus the coroutine it self can force the processor to stop suspend execution of the coroutine to start working on other routines. This is done independently of a scheduler.
 
 ### Which one of these do `pthread_create()` (C/POSIX), `threading.Thread()` (Python), `go` (Go) create?

-pthread_create() Starts a new thread in the calling process.

-threading.Thread() Starts a new thread in the calling process.

-go creates a coroutine.
 
 ### How does pythons Global Interpreter Lock (GIL) influence the way a python Thread behaves?

-Global interpreter lock, or GIL, is a mutex that protects access to Python objects, preventing multiple threads from executing Python bytecodes at once. This lock is necessary mainly because CPython's memory management is not thread-safe.
 
 ### With this in mind: What is the workaround for the GIL (Hint: it's another module)?

-Side-stepping can be used to create multiple processes -GIL Workaround Share memory between the interpreters using memory mapping
 
 ### What does `func GOMAXPROCS(n int) int` change? 

-Gomaxprocs sets the maximum number of cpus that can be executing simultaneously and returns the previous setting. If n <1 , ut does not change th current setting.The number of logical cpus on the local machine can be queried with Numcpu
