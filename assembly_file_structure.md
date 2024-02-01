# Assembly File Structure

---

I will be working on a template **Hello World!** Assembly code.

Code: nasm
```
    global _start

    section .data
message: db     "Hello HTB Academy!"

    section .text

_start:
    mov    rax, 1
    mov    rdi, 1
    mov    rsi, message
    mov    rdx, 18
    syscall

    mov    rax, 60
    mov    rdi, 0
    syscall
```

### Assembly File Structure

![alt text](/images/assembly_file_structure.png)

Looking at the vertical parts of the code, each line has three elements:
1. Labels
2. Instructions
3. Operands

1. global _start = This is a **directive** that directs the code to start executing at the _start label defined below
2. section .data = This is a **data** section, which should contain all of the variables
3. section .text = This is the **text** section containing all of the code to be executed

Both the .data and .text sections refer to the data and text memory segments, in which these instructions will be stored

### Directives

Assembly code is line-based, the file is processed line-by-line, executing the instruction of each line.
We see at the first line a directive global _start, which instructs the machine to start processing the instructions after the _start label. So the machine goes to the _start label and starts executing the instructions there

### Variables

