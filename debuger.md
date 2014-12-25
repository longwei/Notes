valgrind reading and interpreting binary instruction and simulate execution.
but this way it will slow the application down.

the key point here is in linux:
parent process can get additional information about their children, and can ptrace it. so the debugger will be the debugger process, and processes and adpot a child.

ptrace allow parent to rw momory, cpu register, system events, and control of its execution and signal handling.

so the magic is the ptrace on its children process

how about break point? Is it part of ptrace.
No.
1. debugger write a invalid instruction at this location
2. when the application reach the invalid instruction, it will not crashed but give a control back via a interrupt, 
3. then in the SIGTRAP signal is sent to process, then to its parent, our debuger
4. then if the ip is breakpoint list, then we got to a break point.
5. write correct instruction back and single step it.

