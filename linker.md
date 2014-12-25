compiler side:
A definition of a variable induces the compiler to reserve some space for that variable, and possibly fill that space with a particular value.
A definition of a function induces the compiler to generate code for that function.

and declaration promise the compiler that this symbol is someplace else.

then we got a .o file with code and data(global variables)
the compiler leave a blank when see a declaration without implentation.

linker side:
filling the blank, relocate

loader side:
1. load code/ text segment
2. bss to save space on disk

reused? make it a library:
static: 
order of the events: cyclic dependency:
shared:
if the linker find the definition is in a shared library, then it doesn't inlcude in the final executable, but recored the name of the library, on run time, os pull the code of library and joing all part before main function is run. (nm & ldd)

name mangleing
dynamic loaded library: even more defer linking.(dlopen)