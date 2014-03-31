Computer Architecture
=====================


###AC Final Exam Questions

1. Von Neumann architecture.  Computer components.
2 .CPU basics. The main components and their interactions with the memory system and the input/output devices.
3. Instruction cycle.
4. I8086 microprocessor architecture. EU and BIU. 
5. General purpose registers and segment registers of I8086.
6. Special purpose registers of I8086.
7. Instruction set architecture. Basic concepts.
8. Main memory model. Addresses. Instructions and data storing principals.
9. Memory segmentation. Physical address calculation.
10. Instruction format.
11. Data transfer instructions.
12. Arithmetic instructions.
13. Unconditional and conditional transfer instructions.
14. Iteration control instructions. Processor control instructions. Execution control instructions.
15. Logic instructions.
16. Shift instructions.
17. Procedures. The basic mechanism.  CALL and RET Operations.
18. Interrupts. Interrupt sources. Interrupt routine.
19. Memory hierarchy. Memory parameters.
20. Memory chip organization.
21. Memory subsystems.
22. I8086 minimum mode interface signals. 
23. Physical organization of main memory. Low and high banks.
24. Input–Output system. Basic concepts.
25. Programmed I/O
26. Interrupt-driven I/O
27. Bus arbitration in Interrupt-driven I/O
28. Direct memory access (DMA)
29. Bus Arbitration in DMA mode. Centralized and decentralized arbitration 


###1. Von Neumann architecture.  Computer components.

Virtually all contemporary computers are based on concepts developed by John von Neumann.
Such design is based on 3 concepts:

1. data and instructions are stored in a single read-write memory;
2. the contents of this memory are addressable by locations without regard to the type
of data contained there;
3. Execution occurs in a sequential way from one instruction to the next.

![Fig. 1](http://i.imgur.com/SJlOpNO.png)

This is the basic for von Neumann architecture. According to it the computer consists
of:
* CPU(Central Processing Unit);
  * Control unit;
  * AU (Arithmetic and logic unit);
  * Registers.
* Main memory;
* I/O system.

CPU and Main Memory forms a central unit.
A central unit, I/O system and a set of system programs forms a Computer.
A computer and a peripheral devices forms a computer system or a microcomputer system(if
CPU represents a microprocessor).



