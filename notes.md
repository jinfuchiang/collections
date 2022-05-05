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

#### Deal with MMaped Self-modifing Code
- Don't add PROT_EXEC flag before you has completed the code. Because add PROT_EXEC flag will put the code into instruction cache. Modify code after adding PROT_EXEC flag will not invalidate the corresponding i-cahce. So the code you run is not what you want.
- Typically, you should first mmap data page with PROT_READ and PROT_WRITE flags. After you completed the code, use **mprotect** to add PROT_EXEC flag and run it.

#### Byte Array Pitfall
- Char type in C is one byte length, so char type can be used to represente byte and char array can be used to represent byte array.
- But char array is also used as C-string, especially C support writing statement like this `char str[] = "Hello World"`. This statement will automatically append a zero in the end of array.
- If we forget this feature, it may cause problems.
```C++
constexpr char src[] = "\x00\x04\x00\xd1"; // painful to write {'\x00', '\x04\', '\x00', '\xd1'}
memcpy(dst, src, sizeof(src)); // Bad! Will copy the trailling-zero to dst
```
There are enough caveats about the differences between strlen and sizeof when it comes to C-string, but not for byte array(or char []).
Instead of sizeof(), use strlen(). Or don't use char[], use std::string.

#### 查看指定系统调用的两种方式
1. strace -e: only trace given system call
```
strace -e execve,futex ./lock.py
```
2. Use grep "or"
```
strace ./lock.py |& grep "trace\|futex"

```
1通常比2好，1适用于死锁，2则不行。

#### C++ pitfall
```C++
int main() { int i = i; }
```
Above is a valid cpp program. ~~It evaluates as (i) int i (ii) i = i in that order.~~ [It's an UB](https://stackoverflow.com/questions/23415661/has-c-standard-changed-with-respect-to-the-use-of-indeterminate-values-and-und).
