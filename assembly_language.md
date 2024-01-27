# Assembly Language

---

Assembly code `add rax, 1` is more intuitive and easier to remember than its equivalent machine shellcode `4883C001` and its binary machine code `01001000 10000011 11000000 00000001` 

Machine code is often represented as **Shellcode**. Shellcode can be translated back to its Assembly counterpart and can also be loaded directly ito memory as binary instructions to be executed.

![alt text](/images/compilation.png)

**Interpreted Language**
Code: python
`print("Hello World!")`

**High Level Language**
Code: C
```
#include <unistd.h>

int main()
{
    write(1, "Hello World!", 12);
    _exit(0);
}
```

**Assembly**
Code:: nasm
```
mov rax, 1
mov rdi, 1
mov rsi, message
mov rdx, 12
syscall

mov rax, 60
mov rdi, 0
syscall
```

When the `write` syscall is called in C or Assembly, both are using `1`, the text, and `12` as the arguments. 

**shellcode**
```
48 c7 c0 01
48 c7 c7 01
48 8b 34 25
48 c7 c2 0d
0f 05

48 c7 c0 3c
48 c7 c7 00
0f 05
```

**machine code**
Code: binary
```
01001000 11000111 11000000 00000001
01001000 11000111 11000111 00000001
01001000 10001011 00110100 00100101
01001000 11000111 11000010 00001101 
00001111 00000101

01001000 11000111 11000000 00111100 
01001000 11000111 11000111 00000000 
00001111 00000101
```

A CPU uses different electrical charges for a 1 and 0, and hence can calculate these instructions from the binary data once it recieves them

