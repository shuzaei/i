# i

A minimal instruction set for a simplest cpu.

## Registers

4 bit 2 registers
- R1
- R2

CP is hidden yet changeable with a jump instruction.

## Memory

4 bit 16 memory cells
- X0
- X1
- X2
- X3
- X4
- X5
- X6
- X7
- X8
- X9
- XA
- XB
- XC
- XD
- XE
- XF

## Instruction Set

- NAND
  - R1 = R1 NAND R2
- MOV A B 
  - A = B, [] is raw value (e.g. MOV [1] 2 -> X2 = 1)
  - A, B can be R1, R2, 0-F, [0-F]
- JMP
  - if R1 == 0, CP = R2

All instructions are within 12 bits.

Instruction : 2 bits
Indirect addressing : 1 bit for each operand
Operand : 4 bits

2 + 1 + 1 + 4 + 4 = 12 bits

## Instructions

All instructions in the given program are stored in a virtual memory, which is outside of the 16 memory cells. The program counter (CP) is used to point to the current instruction.

Due to the fact that the program counter is limited to 4 bits, the program can only have 16 instructions.

## Example

Store X1 AND X2 in X3

```
MOV R1 1
MOV R2 2
NAND
MOV R1 R2
NAND
MOV 3 R1
```

