Computer Architecture
=====================


###AC MidTerm Exam Questions

1. Adressing Modes
2. Memory Organization
3. Flags/Registers
4. Program


### Addressing Modes

The different ways in which operands can be addressed are called the addressing modes.
Addressing modes available in 8086 are:

####1. immediate addressing mode:

The value of the operand is immediately available in the instruction itself. Immediate
operand represents constant data a bite or a word in 2’s complement word.

```asm
# Example 0.14
mov al 48h, (al) Ã 01001000
mov cx, 1234h
XOR al, 1
al = 1111 1111+
1
1111 1110
al = 1111 1111
+ 1
1111 1110
and ax, 8000H check the value of MSB
```

Advantages:
No memory references for operand are needed.
Disadvantage:
The size of the operand is limited.


####2. register addressing mode:

To access the content of the register it is necessary to specify the name of the register.
The restriction is that both operands must be of the same size.

```asm
#Example 0.15
mov bl, dh – (bl) Ã (dh)
add cx, SI – (cx) Ã (cx) + (SI)
```

Advantage:
The instruction is faster because no memory access is needed, that’s why most of used
operands are keep in registers.
Disadvantage:
An limited number of general registers.


####3. direct addressing mode(displacement only):

In this addressing mode the address field contains the effective address(EA) of the operand.
It consists of 16 bit constant that represents the displacement from the base of the segment.


![ex. 16](http://i.imgur.com/K9fSBJV.png)


####4. register indirected addressing mode:

In this case in the instruction is included the name of the register that hold the ES(effective
address) of the operand. If the register holds this address it is include in square brackets
[BX].

![ex 17](http://i.imgur.com/HNW6ZrG.png)

####5. base addressing mode:

In this case the effective address is calculated using a displacement and a memory address
from BP(base pointer) or BX(base register).

![ex 18](http://i.imgur.com/cl9sZuM.png)

####6. index addressing mode:

In this case the address field contain the main memory address and the register SI or DI
contains a displacement from that address.

```asm
#Example 0.19
move as, disP[SI]
move ax, disP[DI]
```

It is useful in case of iterative operations .. SI or DI specifies the certain element in the
array

```asm
#Example 0.20
inc DI; increment DI
. . .
mov ax, xDI
. . .
```

####7. base index addressing mode:

This is the combination .. . It can be in the following 4 forms:

1. mov al, [bx,SI] – DS: [BX + SI]
2. mov al, [bx,DI] – DS: [BX+ DI]
3. mov al, [bp, SI] – SS: [BP + SI]
4. mov al, [bp, DI] – SS: [BP + DI]

It is useful in matrix array, bi-dimensional array.

####8. base index class displacement addressing mode:

Displacement is and 8 or 16 - bit constant. We add a disP to the previous addressing
mode:

1. mov al, disP[bx,SI] – DS: [BX + SI]
2. mov al, disP[bx,DI] – DS: [BX+ DI]
3. mov al, disP[bp, SI] – SS: [BP + SI]
4. mov al, disP[bp, DI] – SS: [BP + DI]

 
###Memory Organization

**Memory organization** defines how instructions interact with the memory, and also how different parts of memory interact with each other.

Memory hierarchy in a computer system

**Main Memory:** memory unit that communicates directly with the CPU (RAM)
**Auxiliary Memory:** device that provide backup storage (Disk Drives)
**Cache Memory:** special very-high-speed memoryto increase the processingspeed (Cache RAM)

![memory](http://i.imgur.com/yCEH29r.png)

**Multiprogramming** enables the CPU to process a numberof independent program concurrently.
**Memory Management System** supervises the flow of information between auxiliary memoryand main memory.

###Flags/Registers

**Flags Register** – determines the current state of the processor and it is
also called processor status word (PCW). It is a 16-bit register but only 9 bits are used, 6-bits
represents conditions flags and 3-bits control flags

![flags](http://i.imgur.com/S6XBEb2.png)

* CF(Carry Flag) – Represents the carry bit after a 16-bit or 8-bit addition or represents
the borrowed after subtraction.
* PF(Parity Flag) – is equal to 1 if in the lower 8-bit result the number of ones is even.
* AF(Auxiliary Flag) – it represents the carry from the lower 4-bits(nibble) in the byte
and it is used in BCD(Binary Coded Decimals) operations.
* ZF(Zero Flag) – is equal to 1 if the result is equal to zero.
* SF(Sign Flag) – is equal to 1 if the result is negative. This Flag always takes the
value of the MSB(Most Significant Bit).
* OF(Overflow Flag) – is equal to 1 when there is a sign over flow. This happens the
sign bit of the result differs from the signs of the operands. Signs of the operands must
be equal(for Serj).
* CF(Control Flags):
    * TF(Trap Flag) – is equal to 1: in this case the interrupts is generated that allows
the O-chip debugging of the program step by step. For each step of a program the
state of all registers are stored.
    * IF(Interrupt-enable Flag) – it equals to 1 when the processor reacts to the interrupts, and
it equals to 0 when interrupts are masked. 2 extractions can be used to set AF:
      * CLI – clear interrupt
      * STI – set interrupt
* DF(Direction Flag) – equal to 1: the processing in string operations is done
backward. Equal to 0: the processing is done.

####Addition in Hexadecimal 


```


To do addition, you do it just like normal addition.  Line the
numbers up, start by adding the one's digit and carry the 1 if there
is one.


E.g.

    182AB
  + 5FCAA
 ---------

First, add the one's digit: B+A = 15, so I carry the 1:

       1
    182AB
  + 5FCAA
 ---------
        5

Now, add the ten's digit: A+A = 14, plus the 1 I carried = 15. 
Remember to carry the 1 again:

      11
    182AB
  + 5FCAA
 ---------
       55

Now, add the hundred's digit: 2+C = E, plus the 1 I carried = F:

      11
    182AB
  + 5FCAA
 ---------
      F55

Now, add the thousands digit: 8+F = 17, carry the 1:

    1 11
    182AB
  + 5FCAA
 ---------
     7F55

Now, add the last digit: 1+5 = 6, plus the 1 I carried = 7:

    1 11
    182AB
  + 5FCAA
 ---------
    77F55

So:

  182AB + 5FCAA = 77F55
  
```
####Registers

**processor register** is a small amount of storage available as part of a CPU or other digital processor. Such registers are (typically) addressed by mechanisms other than main memory and can be accessed more quickly. Almost all computers, load-store architecture or not, load data from a larger memory into registers where it is used for arithmetic, manipulated, or tested, by some machine instruction. Manipulated data is then often stored back in main memory, either by the same instruction or a subsequent one. Modern processors use either static or dynamic RAM as main memory, the latter often being implicitly accessed via one or more cache levels. A common property of computer programs is locality of reference: the same values are often accessed repeatedly and frequently used values held in registers improves performance. This is what makes fast registers (and caches) meaningful.

Processor registers are normally at the top of the memory hierarchy, and provide the fastest way to access data. The term normally refers only to the group of registers that are directly encoded as part of an instruction, as defined by the instruction set. However, modern high performance CPUs often have duplicates of these "architectural registers" in order to improve performance via register renaming, allowing parallel and speculative execution. Modern x86 is perhaps the most well known example of this technique.[1]

Allocating frequently used variables to registers can be critical to a program's performance. This register allocation is either performed by a compiler, in the code generation phase, or manually, by an assembly language programmer.

####Categories of registers

Registers are normally measured by the number of bits they can hold, for example, an "8-bit register" or a "32-bit register". A processor often contains several kinds of registers, that can be classified accordingly to their content or instructions that operate on them:

* User-accessible registers – instructions that can be read or written by machine instructions. The most common division of user-accessible registers is into data registers and address registers.
  * Data registers can hold numeric values such as integer and, in some architectures, floating-point values, as well as characters, small bit arrays and other data. In some older and low end CPUs, a special data register, known as the accumulator, is used implicitly for many operations.
  * Address registers hold addresses and are used by instructions that indirectly access primary memory.
    * Some processors contain registers that may only be used to hold an address or only to hold numeric values (in some cases used as an index register whose value is added as an offset from some address); others allow registers to hold either kind of quantity. A wide variety of possible addressing modes, used to specify the effective address of an operand, exist.
    * The stack pointer is used to manage the run-time stack. Rarely, other data stacks are addressed by dedicated address registers, see stack machine.
  * General purpose registers (GPRs) can store both data and addresses, i.e., they are combined Data/Address registers and rarely the register file is unified to include floating point as well.
  * Conditional registers hold truth values often used to determine whether some instruction should or should not be executed.
  * Floating point registers (FPRs) store floating point numbers in many architectures.
  * Constant registers hold read-only values such as zero, one, or pi.
  * Vector registers hold data for vector processing done by SIMD instructions (Single Instruction, Multiple Data).
  * Special purpose registers (SPRs) hold program state; they usually include the program counter, also called the instruction pointer, and the status register; the program counter and status register might be combined in a program status word (PSW) register. The aforementioned stack pointer is sometimes also included in this group. Embedded microprocessors can also have registers corresponding to specialized hardware elements.
  * In some architectures, model-specific registers (also called machine-specific registers) store data and settings related to the processor itself. Because their meanings are attached to the design of a specific processor, they cannot be expected to remain standard between processor generations.
  * Memory Type Range Registers (MTRR)
* Internal registers – registers not accessible by instructions, used internally for processor operations.

