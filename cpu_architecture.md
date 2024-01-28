# CPU Architecture

---

The CPU is the main processing unit within a computer, it contains:
- **Control Unit (CU)**
    - Responsible for moving and controlling data
- **Arithmetic/Logic Unit (ALU)**
    - Responsible for various arithmetics and logical calculations as requested by a program through the assembly instructions

**Instruction Set Architecture (ISA)**
- **RISC**
    - based on processing more simple instructions, which takes more cycles, but each cycle is shorter and takes less power
- **CISC**
    - based on fewer, more complex instructions, which can finish the requested instructions in fewer cycles, but each instruction takes more time and power to be processed

### Clock Speed & Clock Cycle

--- 

**Hertz**
- The frequency in which the cylces occur is counted in cylces per second
- 3.0 GHz, runs 3 billion cycles every second (per core)

### Instruction Cycle

--- 

An **Instruction Cycle** is the cycle it takes the CPU to process a single machine instruction.

![alt text](/images/instruction_cycle.png)

| Instruction | Description |
| ----- | ----- |
| 1. Fetch | Takes the next instruction's address from the **Instruction Address Register (IAR)**, which tells it where the next instruction is located |
| 2. Decode | Takes the instruction for the IAR, and decodes it from binary to see what is required to be executed |
| 3. Execute | Fetch instruction operands from register/memory, and process the instruction in the ALU or CU |
| 4. Store | Store the new value in the destination operand |

```
All the stages in the instruction cycle are carried out by the Control Unit, except when arithmetic instructions need to be executed "add,sub,...etc", which are executed by the ALU
```

![alt text](/images/one_instruction_cycle.png)

Each instruction cycle takes multiple clock cycles to finish. Once a single instruction cycle ends, the CU increments to the next instruction and runs the same cycle on it, and so on.

assembly instruction `add rax, 1`:
1. Fetch the instruction from the rip register, `48 83 C0 01`
2. Decode `48 83 C0 01` to know it needs to perform add of 1 to the value at rax
3. Get the current value at rax (by CU), add 1 to it (by the ALU)
4. Store the new value back to rax

modern processers can process multiple instructions in parallel, using multi-thread and multi-core designs

### Processor Specific

---

The same machine code performs entirely different instructions on each processor.
64-bit x86, ARM

This is becuase each process type has a different low-level assembly language architecture known as Instruction Set Architectures (ISA)
- `add rax, 1`
- `add r1, r1, 1`


