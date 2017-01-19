# Reverse-Engineering-Journal
I put anything I find interesting regarding reverse engineering in this journal. The date beside each heading denotes the start date that I added the topic, but most of the time I will still be adding bullets to that heading days later. 

### 12/18/16 (General Knowledge) ###
- A hash function is a mathematical process that takes in an arbitrary-sized input and produces a fixed-size result
- First argument to __libc_start_main() is a pointer to main for ELF files
- nm: displays symbols in binary 
- ldd: print shared library dependencies
- To look at instructions starting from pc for stripped binary in gdb: x/14i $pc
- Set hardware breakpoint in GDB: hbreak 
- Set watchpoint in GDB: watch only break on write, rwatch break on read, awatch break on read/write
- Thunk function: simple function that jumps to another function
- ASLR is turned off by default in GDB. To turn it on: set disable-randomization off
- (32 bits Windows exe) FS register points to the beginning of current thread's environment block (TEB). Offset zero in TEB is the head of 
  a linked list of pointers to exception handler functions
- debug registers 0 through 7 (DR0 - DR7) are used to control the use of hardware breakpoints. DR0 through DR3 are used to specify breakpoint addresses, while DR6 and DR7 are used to enable and disable specific hardware breakpoints

### 12/24/16 ([HARD TO REMEMBER] x86 Instructions With Side Effects) ###
- IMUL reg/mem: register is multiplied with AL, AX, or EAX and the result is stored in AX, DX:AX, or EDX:EAX
- IDIV reg/mem: takes one parameter (divisor). Depending on the divisor’s size, div will use either AX, DX:AX, or EDX:EAX as the dividend, and the resulting quotient/remainder pair are stored in AL/AH, AX/DX, or EAX/EDX
- STOS: writes the value AL/AX/EAX to EDI. Commonly used to initialize a buffer to a constant value
- SCAS: compares AL/AX/EAX with data starting at the memory address EDI
- CLD: clear direction flag
- STD: set direction flag
- REP prefix: repeats an instruction up to ECX times
- MOVSB/MOVSW/MOVSD instructions move data with 1, 2, or 4 byte granularity between two addresses. They implicitly use EDI/ESI as the destination/source address, respectively. In addition, they also automatically update the source/destination address depending on the direction flag

