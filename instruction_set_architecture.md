# Instruction Set Architectures

---

An **Instruction Set Architecture (ISA)** specifies the syntax and semantics of the assembly language on each architecture. 

**ISA** consists of the following components:
- Instructions
- Registers
- Memory Addresses
- Data Types

| Component | Description | Example |
| ----- | ----- | -----|
| Instructions | The instructions to be processed in the **opcode operand_list** format. There are usually 1,2, or 3 comma-separated operands | `add rax, 1`, `mov rsp, rax`, `push rax` |
| Registers | Used to store operands, addresses, or instructions temporarily | rax, rsp, rip | 
| Memory Addresses | The address in which data or instructions are stored. May point to memory or registers | 0xffffffffaa8a25ff, 0x44d0, $rax |
| Data Types | The type of stored data | byte, word, double word |

Two main types of ISA's:
1. **Complex Instruction Set Computer (CISC)** 
    - Used in Intel and AMD processors in most computers and servers
2. **Reduced Intsruction Set Computer (RISC)**
    - Used in ARM and Apple processors, in most smartphones, and some modern laptops

### CISC

---

One of the earliest ISA's ever developed. Favors more complex instructions to be run at a time to reduce the overall number of instructions. 

For example, suppose we were to add two registers with the `add rax, rbx` instruuction. In that case, a CISC processor can do this in a single 'Fetch-Decode-Execute-Store' instruction cycle, without having to split it into multiple instructions to fetch rax, then fetch rbx, then add them, and then store them in rax, each of which would take its own 'Fetch-Decode-Execute-Store' instruction cycle

Two reasons for the above:
1. To enable more instructions to be executed at once by designing the processor to run more advanced instructions in its core
2. In the past, memory and transistors were limited, so it was preferred to write shorter programs by combining multiple instructions into one

Even though it takes a single instruction cycle to execute a single instruction, as the instructions are more complex, each instruction takes more clock cycles

### RISC

---

Favors splitting instructions into minor instructions, cpu is designed to only handle simple instructions.

`add r1, r2, r3` would fetch r2, then fetch r3, add them, and finally store them in r1. Each one takes a full 'Fetch-Decode-Execute-Store'

It is said that we can build a general-purpose computer with a processor that only supports one instruction!

One advantage of splitting complex instructions into minor ones is having the instructions of the same length 32-bit or 64-bit. This enables the CPU clock speed around the instruction length so that executing each stage in the instruction cycle would always take precisely one machine clock cycle

![alt text](/images/set_clock.png)

RISC processors consume a fraction of the power of CISC which makes these processors ideal for devices that run on batteries, like smartphones and laptops


