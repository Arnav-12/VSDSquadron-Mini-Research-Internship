# VSDSquadron-Mini-Research-Internship

As part of my internship, I'm currently working with the **VSDSquadron Mini RISC-V Development Kit**, a robust platform built on the RISC-V architecture. This project offers an opportunity to dive into embedded systems, exploring how RISC-V integrates into various development workflows. I'm gaining practical, hands-on experience with its core features while applying cutting-edge techniques in embedded system design.

## TASK-1

### LAB-1

The first task assigned was to write a C program that calculates the sum of numbers from 1 to n using gEDIT as a Text Editor.

![s1](https://github.com/Arnav-12/VSDSquadron-Mini-Research-Internship/blob/main/s1.png)
![s2](https://github.com/Arnav-12/VSDSquadron-Mini-Research-Internship/blob/main/s2.png)

Ouput generated : Sum of numbers from 1 to 5 is 15
![s3](https://github.com/Arnav-12/VSDSquadron-Mini-Research-Internship/blob/main/s3.png)

Main File Depicting the Assembly instructions
![s4](https://github.com/Arnav-12/VSDSquadron-Mini-Research-Internship/blob/main/s4.png)
![s5](https://github.com/Arnav-12/VSDSquadron-Mini-Research-Internship/blob/main/s5.png)

The Number of instructions with -O1 method
![s6](https://github.com/Arnav-12/VSDSquadron-Mini-Research-Internship/blob/main/s6.png)

The Number of instructions with -Ofast method

![s7](https://github.com/Arnav-12/VSDSquadron-Mini-Research-Internship/blob/main/s7.png)

## TASK-2

The Second Task assigned was to use Spike Simulation for debugging

Verifying the C code with n=100 with spike simulation
![s10](https://github.com/Arnav-12/VSDSquadron-Mini-Research-Internship/blob/main/s10.png)

Using spike commands for debugging of instructions
![s11](https://github.com/Arnav-12/VSDSquadron-Mini-Research-Internship/blob/main/s11.png)

After implementations of instruction the sp value gets reduced by factor a hexadecimal fector of 10
![s9](https://github.com/Arnav-12/VSDSquadron-Mini-Research-Internship/blob/main/s9.png)

## TASK-3

### RISC-V ISA
A RISC-V ISA is defined as a base integer ISA, which must be present in any implementation, plus
optional extensions to the base ISA. The base integer ISAs are very similar to that of the early RISC
processors except with no branch delay slots and with support for optional variable-length instruction
encodings. A base is carefully restricted to a minimal set of instructions sufficient to provide a RISC-V ISA is defined as a base integer ISA, which must be present in any implementation, plus
optional extensions to the base ISA. The base integer ISAs are very similar to that of the early RISC
processors except with no branch delay slots and with support for optional variable-length instruction
encodings. A base is carefully restricted to a minimal set of instructions sufficient to provide a

### Types of Instruction Formats in RISC-V
RISC-V instructions are organized into five main types based on how operands and data are accessed and manipulated.

RISC-V Instruction Types (R, I, S, B, U, J)
RISC-V instructions are categorized into six main types, each with a specific format for accessing and manipulating operands. The structure of these instructions includes fields like opcode, rd, rs1, rs2, and immediate values, which allow for flexible operation encoding. Below, we outline each instruction type in detail.

1. R-Type (Register-Register) Instruction
Purpose
The R-Type format is used for operations that involve two source registers and a destination register. These instructions typically perform arithmetic or logical operations, where data is read from two registers, processed, and stored in a third register.

Fields
opcode (7 bits): Determines the type of operation (e.g., integer arithmetic, floating-point arithmetic).
funct3 (3 bits): Adds further specificity to the operation, helping distinguish between similar instructions (e.g., add vs. sub).
funct7 (7 bits): Additional control bits that refine the operation further (e.g., indicating shifts or subtractions).
rs1 (5 bits): First source register, providing one operand.
rs2 (5 bits): Second source register, providing the other operand.
rd (5 bits): Destination register where the result is stored.
![s12](https://github.com/Arnav-12/VSDSquadron-Mini-Research-Internship/blob/main/s10.png)

2. I-Type (Immediate) Instruction
Purpose
I-Type instructions perform operations that involve one register and an immediate (constant) value. This type is often used for load instructions, arithmetic with a constant, and setting register values with immediate values.

Fields
opcode (7 bits): Specifies the operation (e.g., load, arithmetic with an immediate).
funct3 (3 bits): Determines the specific operation within the immediate class (e.g., addi for add-immediate, andi for bitwise AND).
rs1 (5 bits): Source register that provides the operand.
rd (5 bits): Destination register for the result.
Immediate (12 bits): Constant value used as an operand, signed or zero-extended depending on the operation.
![s13](https://github.com/Arnav-12/VSDSquadron-Mini-Research-Internship/blob/main/s11.png)

3. S-Type (Store) Instruction
Purpose
S-Type instructions are used for store operations, where data from a register is written to memory. The address is calculated by adding an immediate value to a base address provided by a register.

Fields
opcode (7 bits): Specifies the store operation (e.g., sw for store word).
funct3 (3 bits): Defines the type of store operation (e.g., word, byte).
rs1 (5 bits): Register holding the base address for the store.
rs2 (5 bits): Source register containing the data to store.
Immediate (12 bits): Split into two parts (5 bits and 7 bits), represents the offset added to the base address to get the effective memory location.
![s14](https://github.com/Arnav-12/VSDSquadron-Mini-Research-Internship/blob/main/s12.png)

4. B-Type (Branch) Instruction
Purpose
B-Type instructions enable conditional branching, allowing the program to jump to a different location based on the result of a comparison. This comparison is between two registers, with a branch taken if the specified condition is met.

Fields
opcode (7 bits): Indicates a branch operation.
funct3 (3 bits): Specifies the type of comparison (e.g., equal, not equal, less than).
rs1 (5 bits): First source register for comparison.
rs2 (5 bits): Second source register for comparison.
Immediate (12 bits): Offset added to the program counter (PC) if the branch is taken. This offset is split into multiple parts within the instruction encoding.

![s15](https://github.com/Arnav-12/VSDSquadron-Mini-Research-Internship/blob/main/s13.png)

5. U-Type (Upper Immediate) Instruction
Purpose
U-Type instructions are used to load a 20-bit immediate value into the upper 20 bits of a register, typically for setting larger immediate values or addresses. This format is often used with instructions that deal with high-order constants.

Fields
opcode (7 bits): Indicates an upper immediate operation (e.g., lui for Load Upper Immediate).
rd (5 bits): Destination register for the immediate value.
Immediate (20 bits): The upper 20-bit immediate value to load, with the lower 12 bits of the register typically cleared.

![s16](https://github.com/Arnav-12/VSDSquadron-Mini-Research-Internship/blob/main/s14.png)

6. J-Type (Jump) Instruction
Purpose
J-Type instructions support unconditional jumps to an address computed by adding an immediate value to the current program counter (PC). They are often used for function calls and unconditional jumps.

Fields
opcode (7 bits): Indicates a jump operation (e.g., jal for Jump and Link).
rd (5 bits): Destination register to store the return address (PC + 4).
Immediate (20 bits): Offset added to the current PC to get the jump target address. The immediate field is split across the instruction format.
![s17](https://github.com/Arnav-12/VSDSquadron-Mini-Research-Internship/blob/main/s15.png)


