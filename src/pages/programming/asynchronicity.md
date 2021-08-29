# Asynchronicity

A statement can be either executed synchronously or asynchronously. Synchronous
code is run serially while asynchronous code is run in parallel. Asynchronousity
can be achieved using e.g. event loops or threads.

## Event loops

An event loop is a queue of items waiting to be run. The items are then run one
by one. Thus if one item takes a long time, the event loop will wait for it -
blocking other items from being run. This is called blocking. This is contrast
to threads where one thread cannot block another. Threads on the other hand is
more startup overhead.

## Threads

A thread is typically run on its own by the operating system, different from the
thread running the application code. Thus one can run threads on different CPU
cores. However, this can give raise to e.g. race conditions.

### Threads vs processes

There is a difference between a process and a thread. A process is run in a
thread. Threads have shared memory. A process has its own virtual resources,
process identifier etc.
