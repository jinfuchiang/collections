- LR: Link Register, used to store return address, is more efficient than store address on stack. 机器级的函数调用支持。
- 为什么调用extern的函数时需要trampoline？跳转距离太远，一条指令放不下callee的地址信息。比如，AArch64中指令长度统一为4字节，但表示完整地址空间虚8字节。
- pre-increment v.s. post-increment
```assembly
STP X0, X1, [SP, #-16]! ; push
LDP X0, X1, [SP], #16 ; pop
```
