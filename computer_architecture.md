# Computer Architecture

---

Most modern computers are built on **Von Neumann Architecture**, which was developed back in 1945.

This architecture executes machine code to perform specific algorithms.  Consisting of these elements:

- Central Processing Unit (CPU)
- Memory Unit
- Input/Output Devices
    - Mass Storage Unit
    - Keyboard
    - Display

CPU consists of three main components:
- Control Unit (CU)
- Arthmetic/Logic Unit (ALU)
- Registers

![alt text](/images/computer_elements.png)

Assembly languages mainly work with CPU and memory. 

### Memory

---

Memory is where **temporary** data and instructions of currently running programs are located. 
Two main types of memory:
1. **Cache**
2. **Random Access Memory (RAM)**

#### Cache

Cache memory is usually located within the CPU itself and is extremely fast compared to RAM.

| Level | Description |
| ---- | ----- |
| Level 1 Cache | Usually in Kilobytes, the fastest memory, located in each CPU core. (Only registers are faster.) |
| Level 2 Cache | Usually in megabytes, extremely fast(but slower than L1), shared between all CPU cores. |
| Level 3 Cache | Usually in megabytes (larger than L2), faster than RAM but slower than L1/L2. (Not all CPUs use L3) |

#### RAM

RAM is much larger than cache memory. Accessing data from RAM addresses takes many more instructions.

Retreiving instructions from registers takes one clock cycle.
Retreiving from L1 cache takes a few clock cycles.
Retreiving from RAM takes around 200 cycles.

When a program is run, all of its data and instructions are moved from the storage unit to the RAM to be accessed when needed by the CPU.

RAM is split into four main **segments**:

| Segment | Description |
| --- | ---- |
| Stack | Has a Last-in First-out (LIFO) design and is fixed in size. Data in it can only be accessed in a specific order by push-ing and pop-ing data. |
| Heap | Has a hierachical design and is therefore much larger and more versatile in storing data, as data can be stored and retrieved in any order. However, this makes the heap slower than the Stack |
| Data | Has two parts: **Data**, which is used to hold variables, and **.bss**. which is used to hold unassigned variables (i.e., buffer memory for later allocation) |
| Text | Main assembly instructions are loaded into this segment to be fetched and executed by the CPU |

**Each application is allocated its Virtual Memory when it is run.**  Each application would have its own stack, heap, data, and text segments.

### IO/Storage 

---

The processor can access and control IO devices using **Bus Interfaces**, which act as "highways" to transfer data and addreesses, using electrical charges for binary data.

Each Bus has a capacity of bits (or electrical charges) it can carry simultaneously. Usually a multiple of 4-bits, ranging up to 128 bits.

**Bus interface lines on motherboard**
![alt text](/images/bus.png)

The storage unit is the slowest to access, accessing them through bus interfaces like SATA or USB takes much longer to store and retrieve the data.

Shift from classic magnetic storage units, like tapes or Hard Disk Drives (HDD), to Solid-State Drives (SSD) in recent years. SSD;s utilize a similar design to RAM, using non-volatile circuitry that retains data even without electricity. This made storage units much faster.

