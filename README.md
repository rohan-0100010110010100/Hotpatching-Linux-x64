# Hotpatching-Linux-x64
Hotpatching methodology &amp; Implementaion in order to build software stub.

Hotpatching is used in the software application to patch the software at the runtime, so that you do not need to quit the entire applications.

The hotpatching strategy used in linux x64 is as follows:

* Choose the offset of the functions which needed to be replaced in the program.

* Pre-design the programs such that few offsets(5 or 6 offsets) before the target function be all ```nop``` operation.

* Select the appropriate active page which constains the function, this can be done by making all the functions to be aligned by a fixed offset say 8 bytes/16 bytes. In code it is done by using __attribute__() extension 

* Then page containing the target function can be achieved by performing logical AND of the target function & complement of 0xffff.

* On x64 the page is typically 4K, thus all the target functions should be organized as if all target function are in one page.

* We used a thread-based shared memory model to execute our hotpatch our program.

* Make sure that the function is 8 byte aligned before replacing the function with new function.

## Hotpatching & Hooking has two benefits:

* You don’t have to search for the function definition in the library, such as libc (glibc is the GNU C Library, and libc is almost half of the size of glibc) and change it. Seriously, this is a very nasty technical task (at least for me!).
* You don’t need to recompile the library’s source code.
* Hooking & hotpatching are closely reated to each other, but in GCC 8.0 the malloc hookig is disabled.

## Demonstration of Code ##

This is a simple program to show hotpatching.

