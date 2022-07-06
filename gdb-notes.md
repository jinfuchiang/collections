#### 查看内存区域
`x/56wx`：w 代表 4 字节，x 代表 16 进制显示，56 代表显示 56 个 4 字节。显示效果为：每行 4 列（16 Byte），共 14 行。
#### hook-stop 是什么
The hook function hook-stop is a special definition that GDB calls at every breakpoint event. This means that you can use it to call your user-defined functions each time GDB stops (after a breakpoint, after each next/nexti, etc.).---[ref](https://www.adacore.com/gems/gem-120-gdb-scripting-part-2)

gdb里的hook函数与某些事件绑定，当绑定事件发生时，该函数被触发执行。类似的还有hook-run、hook-continue函数。

程序执行时忽略SIGUSR1信号引起的运行停止
```
(gdb) define hook-run
> handle SIGUSR1 nostop
> end
```
汇编调试时, 跟踪显示汇编以及指定寄存器的信息
```
(gdb) define hook-stop
Type commands for definition of "hook-stop".
End with a line saying just "end".
>p /x $eax
>p /x $ebx
>disas $rip + 5
>end
```
#### 如何查看进程pid
```
(gdb) info inferiors 
  Num  Description       Executable        
* 1    process 2782      /home/sirius/competitive-programming/a.out
```
#### 如何查看进程内存分布
示例程序
```C
#include <stdio.h>
int array[(1<<30)];
int main()
{
	printf( "hello world\n");
	return 0;
}
```
1. 使用`info proc mappings`
```
(gdb) info proc mappings 
process 2782
Mapped address spaces:

          Start Addr           End Addr       Size     Offset objfile
           0x8000000          0x8001000     0x1000        0x0 /home/sirius/competitive-programming/a.out
           0x8001000          0x8002000     0x1000     0x1000 /home/sirius/competitive-programming/a.out
           0x8002000          0x8003000     0x1000     0x2000 /home/sirius/competitive-programming/a.out
           0x8003000          0x8004000     0x1000     0x2000 /home/sirius/competitive-programming/a.out
           0x8004000          0x8005000     0x1000     0x3000 /home/sirius/competitive-programming/a.out
           0x8005000        0x108005000 0x100000000        0x0 
      0x7fffff5b0000     0x7fffff5d5000    0x25000        0x0 /usr/lib/x86_64-linux-gnu/libc-2.31.so
      0x7fffff5d5000     0x7fffff74d000   0x178000    0x25000 /usr/lib/x86_64-linux-gnu/libc-2.31.so
      0x7fffff74d000     0x7fffff797000    0x4a000   0x19d000 /usr/lib/x86_64-linux-gnu/libc-2.31.so
      0x7fffff797000     0x7fffff798000     0x1000   0x1e7000 /usr/lib/x86_64-linux-gnu/libc-2.31.so
      0x7fffff798000     0x7fffff79b000     0x3000   0x1e7000 /usr/lib/x86_64-linux-gnu/libc-2.31.so
      0x7fffff79b000     0x7fffff79e000     0x3000   0x1ea000 /usr/lib/x86_64-linux-gnu/libc-2.31.so
      0x7fffff79e000     0x7fffff7a2000     0x4000        0x0 
      0x7fffff7b0000     0x7fffff7b1000     0x1000        0x0 /usr/lib/x86_64-linux-gnu/ld-2.31.so
      0x7fffff7b1000     0x7fffff7b3000     0x2000     0x1000 /usr/lib/x86_64-linux-gnu/ld-2.31.so
      0x7fffff7b3000     0x7fffff7b4000     0x1000     0x3000 /usr/lib/x86_64-linux-gnu/ld-2.31.so
      0x7fffff7b4000     0x7fffff7b5000     0x1000     0x4000 /usr/lib/x86_64-linux-gnu/ld-2.31.so
      0x7fffff7b5000     0x7fffff7b6000     0x1000     0x5000 /usr/lib/x86_64-linux-gnu/ld-2.31.so
      0x7fffff7b6000     0x7fffff7b7000     0x1000     0x6000 /usr/lib/x86_64-linux-gnu/ld-2.31.so
      0x7fffff7b7000     0x7fffff7b8000     0x1000     0x7000 /usr/lib/x86_64-linux-gnu/ld-2.31.so
      0x7fffff7b8000     0x7fffff7c6000     0xe000     0x8000 /usr/lib/x86_64-linux-gnu/ld-2.31.so
      0x7fffff7c6000     0x7fffff7c7000     0x1000    0x16000 /usr/lib/x86_64-linux-gnu/ld-2.31.so
      0x7fffff7c7000     0x7fffff7c8000     0x1000    0x17000 /usr/lib/x86_64-linux-gnu/ld-2.31.so
      0x7fffff7c8000     0x7fffff7d3000     0xb000    0x18000 /usr/lib/x86_64-linux-gnu/ld-2.31.so
      0x7fffff7d3000     0x7fffff7d4000     0x1000    0x23000 /usr/lib/x86_64-linux-gnu/ld-2.31.so
      0x7fffff7d4000     0x7fffff7db000     0x7000    0x24000 /usr/lib/x86_64-linux-gnu/ld-2.31.so
      0x7fffff7db000     0x7fffff7dc000     0x1000    0x2b000 /usr/lib/x86_64-linux-gnu/ld-2.31.so
      0x7fffff7dd000     0x7fffff7de000     0x1000    0x2c000 /usr/lib/x86_64-linux-gnu/ld-2.31.so
      0x7fffff7de000     0x7fffff7df000     0x1000    0x2d000 /usr/lib/x86_64-linux-gnu/ld-2.31.so
      0x7fffff7df000     0x7fffff7e2000     0x3000        0x0 
      0x7fffff7ef000     0x7ffffffef000   0x800000        0x0 [stack]
      0x7ffffffef000     0x7fffffff0000     0x1000        0x0 [vdso]
```
2. 使用 `cat /proc/<pid>/maps`
```
(gdb) !cat /proc/2782/maps
08000000-08001000 r--p 00000000 00:00 323488                     /home/sirius/competitive-programming/a.out
08001000-08002000 rwxp 00001000 00:00 323488                     /home/sirius/competitive-programming/a.out
08002000-08003000 r--p 00002000 00:00 323488                     /home/sirius/competitive-programming/a.out
08003000-08004000 r--p 00002000 00:00 323488                     /home/sirius/competitive-programming/a.out
08004000-08005000 rw-p 00003000 00:00 323488                     /home/sirius/competitive-programming/a.out
08005000-108005000 rw-p 00000000 00:00 0
7fffff5b0000-7fffff5d5000 r--p 00000000 00:00 85659              /usr/lib/x86_64-linux-gnu/libc-2.31.so
7fffff5d5000-7fffff74d000 r-xp 00025000 00:00 85659              /usr/lib/x86_64-linux-gnu/libc-2.31.so
7fffff74d000-7fffff797000 r--p 0019d000 00:00 85659              /usr/lib/x86_64-linux-gnu/libc-2.31.so
7fffff797000-7fffff798000 ---p 001e7000 00:00 85659              /usr/lib/x86_64-linux-gnu/libc-2.31.so
7fffff798000-7fffff79b000 r--p 001e7000 00:00 85659              /usr/lib/x86_64-linux-gnu/libc-2.31.so
7fffff79b000-7fffff79e000 rw-p 001ea000 00:00 85659              /usr/lib/x86_64-linux-gnu/libc-2.31.so
7fffff79e000-7fffff7a2000 rw-p 00000000 00:00 0
7fffff7b0000-7fffff7b1000 r--p 00000000 00:00 85366              /usr/lib/x86_64-linux-gnu/ld-2.31.so
7fffff7b1000-7fffff7b3000 r-xp 00001000 00:00 85366              /usr/lib/x86_64-linux-gnu/ld-2.31.so
7fffff7b3000-7fffff7b4000 rwxp 00003000 00:00 85366              /usr/lib/x86_64-linux-gnu/ld-2.31.so
7fffff7b4000-7fffff7b5000 rwxp 00004000 00:00 85366              /usr/lib/x86_64-linux-gnu/ld-2.31.so
7fffff7b5000-7fffff7b6000 r-xp 00005000 00:00 85366              /usr/lib/x86_64-linux-gnu/ld-2.31.so
7fffff7b6000-7fffff7b7000 rwxp 00006000 00:00 85366              /usr/lib/x86_64-linux-gnu/ld-2.31.so
7fffff7b7000-7fffff7b8000 rwxp 00007000 00:00 85366              /usr/lib/x86_64-linux-gnu/ld-2.31.so
7fffff7b8000-7fffff7c6000 r-xp 00008000 00:00 85366              /usr/lib/x86_64-linux-gnu/ld-2.31.so
7fffff7c6000-7fffff7c7000 rwxp 00016000 00:00 85366              /usr/lib/x86_64-linux-gnu/ld-2.31.so
7fffff7c7000-7fffff7c8000 rwxp 00017000 00:00 85366              /usr/lib/x86_64-linux-gnu/ld-2.31.so
7fffff7c8000-7fffff7d3000 r-xp 00018000 00:00 85366              /usr/lib/x86_64-linux-gnu/ld-2.31.so
7fffff7d3000-7fffff7d4000 r-xp 00023000 00:00 85366              /usr/lib/x86_64-linux-gnu/ld-2.31.so
7fffff7d4000-7fffff7db000 r--p 00024000 00:00 85366              /usr/lib/x86_64-linux-gnu/ld-2.31.so
7fffff7db000-7fffff7dc000 r--p 0002b000 00:00 85366              /usr/lib/x86_64-linux-gnu/ld-2.31.so
7fffff7dd000-7fffff7de000 r--p 0002c000 00:00 85366              /usr/lib/x86_64-linux-gnu/ld-2.31.so
7fffff7de000-7fffff7df000 rw-p 0002d000 00:00 85366              /usr/lib/x86_64-linux-gnu/ld-2.31.so
7fffff7df000-7fffff7e2000 rw-p 00000000 00:00 0
7fffff7ef000-7ffffffef000 rw-p 00000000 00:00 0                  [stack]
7ffffffef000-7fffffff0000 r-xp 00000000 00:00 0                  [vdso]
```
3. 使用`pmap <pid>`
```
(gdb) !pmap 2782
2782:   /home/sirius/competitive-programming/a.out
0000000008000000      4K r---- a.out
0000000008001000      4K rwx-- a.out
0000000008002000      4K r---- a.out
0000000008003000      4K r---- a.out
0000000008004000      4K rw--- a.out
0000000008005000 4194304K rw---   [ anon ]
00007fffff5b0000    148K r---- libc-2.31.so
00007fffff5d5000   1504K r-x-- libc-2.31.so
00007fffff74d000    296K r---- libc-2.31.so
00007fffff797000      4K ----- libc-2.31.so
00007fffff798000     12K r---- libc-2.31.so
00007fffff79b000     12K rw--- libc-2.31.so
00007fffff79e000     16K rw---   [ anon ]
00007fffff7b0000      4K r---- ld-2.31.so
00007fffff7b1000      8K r-x-- ld-2.31.so
00007fffff7b3000      4K rwx-- ld-2.31.so
00007fffff7b4000      4K rwx-- ld-2.31.so
00007fffff7b5000      4K r-x-- ld-2.31.so
00007fffff7b6000      4K rwx-- ld-2.31.so
00007fffff7b7000      4K rwx-- ld-2.31.so
00007fffff7b8000     56K r-x-- ld-2.31.so
00007fffff7c6000      4K rwx-- ld-2.31.so
00007fffff7c7000      4K rwx-- ld-2.31.so
00007fffff7c8000     44K r-x-- ld-2.31.so
00007fffff7d3000      4K r-x-- ld-2.31.so
00007fffff7d4000     28K r---- ld-2.31.so
00007fffff7db000      4K r---- ld-2.31.so
00007fffff7dd000      4K r---- ld-2.31.so
00007fffff7de000      4K rw--- ld-2.31.so
00007fffff7df000     12K rw---   [ anon ]
00007fffff7ef000   8192K rw---   [ anon ]
00007ffffffef000      4K r-x--   [ anon ]
 total          4204708K
``` 
4. 使用readelf读取
Type为LOAD的行，offset代表在文件偏移，VirtAddr每个段的虚拟起始地址，FileSiz代表该段在目标文件所占的大小，MemSiz代表该段在内存空间所占大小。
```
(gdb) !readelf -l a.out 

Elf file type is DYN (Shared object file)
Entry point 0x1060
There are 13 program headers, starting at offset 64

Program Headers:
  Type           Offset             VirtAddr           PhysAddr
                 FileSiz            MemSiz              Flags  Align
  PHDR           0x0000000000000040 0x0000000000000040 0x0000000000000040
                 0x00000000000002d8 0x00000000000002d8  R      0x8
  INTERP         0x0000000000000318 0x0000000000000318 0x0000000000000318
                 0x000000000000001c 0x000000000000001c  R      0x1
      [Requesting program interpreter: /lib64/ld-linux-x86-64.so.2]
  LOAD           0x0000000000000000 0x0000000000000000 0x0000000000000000
                 0x00000000000005f8 0x00000000000005f8  R      0x1000
  LOAD           0x0000000000001000 0x0000000000001000 0x0000000000001000
                 0x00000000000001f5 0x00000000000001f5  R E    0x1000
  LOAD           0x0000000000002000 0x0000000000002000 0x0000000000002000
                 0x0000000000000160 0x0000000000000160  R      0x1000
  LOAD           0x0000000000002db8 0x0000000000003db8 0x0000000000003db8
                 0x0000000000000258 0x0000000100000288  RW     0x1000
  DYNAMIC        0x0000000000002dc8 0x0000000000003dc8 0x0000000000003dc8
                 0x00000000000001f0 0x00000000000001f0  RW     0x8
  NOTE           0x0000000000000338 0x0000000000000338 0x0000000000000338
                 0x0000000000000020 0x0000000000000020  R      0x8
  NOTE           0x0000000000000358 0x0000000000000358 0x0000000000000358
                 0x0000000000000044 0x0000000000000044  R      0x4
  GNU_PROPERTY   0x0000000000000338 0x0000000000000338 0x0000000000000338
                 0x0000000000000020 0x0000000000000020  R      0x8
  GNU_EH_FRAME   0x0000000000002010 0x0000000000002010 0x0000000000002010
                 0x0000000000000044 0x0000000000000044  R      0x4
  GNU_STACK      0x0000000000000000 0x0000000000000000 0x0000000000000000
                 0x0000000000000000 0x0000000000000000  RW     0x10
  GNU_RELRO      0x0000000000002db8 0x0000000000003db8 0x0000000000003db8
                 0x0000000000000248 0x0000000000000248  R      0x1

 Section to Segment mapping:
  Segment Sections...
   00     
   01     .interp 
   02     .interp .note.gnu.property .note.gnu.build-id .note.ABI-tag .gnu.hash .dynsym .dynstr .gnu.version .gnu.version_r .rela.dyn .rela.plt 
   03     .init .plt .plt.got .plt.sec .text .fini 
   04     .rodata .eh_frame_hdr .eh_frame 
   05     .init_array .fini_array .dynamic .got .data .bss 
   06     .dynamic 
   07     .note.gnu.property 
   08     .note.gnu.build-id .note.ABI-tag 
   09     .note.gnu.property 
   10     .eh_frame_hdr 
   11     
   12     .init_array .fini_array .dynamic .got 
```

```
(gdb) help info proc
Show /proc process information about any running process.
Specify any process id, or use the program being debugged by default.
Specify any of the following keywords for detailed info:
  mappings -- list of mapped memory regions.
  stat     -- list a bunch of random process info.
  status   -- list a different bunch of random process info.
  all      -- list all available /proc info.
```
