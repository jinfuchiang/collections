- LR: Link Register, used to store return address, is more efficient than store address on stack. 机器级的函数调用支持。
- 为什么调用 extern 函数时需要 trampoline？跳转距离太远，一条指令放不下 callee 的地址信息。比如，AArch64 中指令长度统一为 4 字节，但表示完整地址空间需要 8 字节。
- pre-increment v.s. post-increment
```assembly
STP X0, X1, [SP, #-16]! ; push
LDP X0, X1, [SP], #16 ; pop
```
#### How to Read pmccntr?
See [here](https://github.com/jinfuchiang/collections/blob/main/snippet.md#user-content-armv7-a).
Note that MCR(write) and MRC(read) instruction don't exist in Armv8 instruction set. So, use MSR(write) and MRS(read) in AArch64.

#### Where to find core dump files?
Use [coredumpctl](https://wiki.archlinux.org/title/Core_dump#Examining_a_core_dump).
