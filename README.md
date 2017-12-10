# os-malloc
This directory contains:

 * myAllocator.c: a first-fit and best-bit allocator
 * myAllocator.h: its header file
 * myAllocatorTest1.c: a test program for the best-bit allocator 
 * malloc.c: a replacement for malloc that uses my allocator
 * test1.c: a test program that uses this replacement malloc

There are two different testers as some implementations of printf
call malloc to allocate buffer space. This causes test1 to behave
improperly as it uses myAllocator as a malloc replacement. In this
case myAllocatorTest1 will function correctly. The only difference
between the programs is that test1 uses myAllocator as a malloc
replacement and myAllocatorTest1 uses myAllocator directly.

Makefile: a fairly portable "makefile", targets "all" and "clean"

To compile: 
~~~
$ make 
~~~

To test it:
~~~
$ ./myAllocatorTest1
~~~

To clean:
~~~
$ make clean
~~~

The cygwin runtime uses malloc() and brk() extensively.  It is
interesting to compare the output of test1 & myAllocatorTest1.  All
those extra allocated regions are being used by cygwin's libraries!

12/10/17 - https://www.youtube.com/watch?v=YcX-awpW9yc was a source to understand how to implement best-fit allocation. Troubleshooted with Ricardo Alvarez, Hector Cervantes, and Tom when my best fit was working like a first-fit allocator. Used the coalescePrev and part of first-fit allocator on resizeRegion.

