# Hotpatching-Linux-x64
Hotpatching methodology &amp; Implementaion in order to build software stub.

Hotpatching is used in the software application to patch the software at the runtime, so that you do not need to quit the entire applications.

The hotpatching strategy used in linux x64 is as follows:

* Choose the offset of the functions which needed to be replaced in the program.

* Pre-design the programs such that few offsets(5 or 6 offsets) before the target function be all ```nop``` operation.

* Select the appropriate active page which constains the function, this can be done by making all the functions to be aligned by a fixed offset say 8 bytes/16 bytes. 

* Then page containing the target function can be achieved by multiplying the offset with the page number.




