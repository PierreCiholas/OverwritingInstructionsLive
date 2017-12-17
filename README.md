# OverwritingInstructionsLive

Imagine that you have some executable memory, with for example an infinite loop using a short jump like that:

NOP
JMP REL8 0xFE (-0x2)

This generate the following shellcode:

0x90, 0xEB, 0xFE

Now, what would happen if another process or another thread was modifying the byte of the destination of the short jump?
Would it be possible that the instruction executes while the destination is BEING overwritten?
For example, 0xFE (-0x2) is 1111 1110 is binary.
Could it happen that this short jump sometimes jumps of 0x1E (0001 1110) because it is currently being overwritten?
Or is that impossible?
Note that I am interested only in knowing the possibility of an incomplete overwrite of a single byte, no more than that.

This program tests just that.
And apparently, it cannot be executed while being only partially overwritten.
