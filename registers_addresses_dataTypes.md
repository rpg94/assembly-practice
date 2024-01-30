# Registers, Addresses, Data Types

---

Module goes over a few assembly elements: **Registers**, **Memory Addresses**, **Address Endianness**, and **Data Types**

### Registers

---

Each CPU core has a set of registers. Registers are the fastest components in any computer as they are built within the CPU core.  Very limited in size and can only hold a few bytes of data at a time.

**Basic Registers**
| Data Registers | Pointer Registers |
| --- | --- |
| rax | rbp |
| rbx | rsp |
| rcx | rip |
| rdx | |
| r8 | |
| r9 | |
| r10 | |

- **Data Registers**: usually used for storing instructions/syscall arguments. The primary data registers are: `rax, rbx, rcx, and rdx` The `rdi` and `rsi` registers also exist and are usually used for the instruction destination and source operands. Secondary data registers that can be used when all previous registers are in use, which are `r8`, `r9`, `r10`
- **Pointer Registers**: are used to store specific important address pointers. The main pointer registers are the Base Stack Pointer `rbp`, which points to the beginning of the Stack, the Current Stack Pointer `rsp`, which points to the current location within the Stack (top of the Stack), and the Instruction Pointer `rip`, which holds the address of the next instruction

### Sub-Registers

---

Each 64-bit register can be further divided into smaller sub-registers containing the lower bits, an one byte 8-bits, 2 bytes 16-bits and 4 bytes 32-bits, Each sub-register can be used and accessed on its own, so we don't have to consume the full 64-bits if we have a smaller amount of data

![alt text](/images/sub_registers.png)

| Size in bits | Size in bytes | Name | Example |
| --- | --- | --- | --- |
| 16-bit | 2 bytes | the base name | ax |
| 8-bit | 1 bytes | base name and/or ends with l | al |
| 32-bit | 4 bytes | base name + starts with the e prefix | eax |
| 64-bit | 8 bytes | base name + starts with the r prefix | rax |

![alt text](/images/sub_register_names.png)

### Memory Addresses 

---

x86 64-bit processors have 64-bit wide addresses that range from `0x0` to `0xffffffffffffffff`
However, RAM is segmented into various regions like the Stack, the heap, and other program and kernel-specific regions. Each memory region has a specific read, write, execute permissions that specify whether we can read from it, write to it, or call an address in it

Whenever an instruction goes through the Instruction Cycle to be executed, the first step is to fetch the instruction from the address it's located at.

![alt text](/images/memory_addresses.png)

lower is slower in the above table. The less immediate the value is, the slower it is to fetch it

### Address Endianness

---

- is the order of its bytes in which they are stored ore retrieved from memory. 
- Two types: **Little-Endian** and **Big-Endian**
- With Little-Endian processors, the little-end byte of the address is filled/retrieved first right-to-left, while the Big-Endian processors, the big-end byte is filled/retrieved first left-to right

- The order in which the bytes are stored/retrieved makes a big difference in output

```
This module will always use little-endian byte order, as it is used with Intel/AMD x86 in most modern operating systems, so the shellcode is always represented right-to-left.
```

- The important thing we need to take from this is knowing that our bytes are stored in memory from right-to-left. So, if we push an address or a string with Assembly, we would have to push it in reverse. Hello would be pushed in reverse: o,l,l,e,H.

### Data Types

---

x86 architecture supports many types of data sizes

| Component | Length | Example |
| --- | --- | --- |
| byte | 8 bits | 0xab |
| word | 16 bits - 2 bytes | 0xabcd |
| double word (dword) | 32 bits - 4 bytes | 0xabcdef12 |
| quad word (qword) | 64 bits - 8 bytes | 0xabcdef1234567890 |

Whenever we use a variable with a certain data type or use a data type with an instruction, both operands should be of the same size

For example, we can't use a variable defined as byte with rax, as rax has a size of 8 bytes. In this case, we would have to use al, which has the same size of 1 byte.

![alt text](/images/size.png)

