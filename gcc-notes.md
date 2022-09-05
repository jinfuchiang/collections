## objdump
### 显示文件二进制
两栏，左栏 hex，右栏 ascii，一行 16 Byte。
```shell
# Display the full contents of any sections requested
objdump -s 
```
配合 -j 可以只显示指定section的二进制
### demangling、不显示指令二进制
```shell
objdump --no-show-raw-insn -dC hello
```
## objcopy
### 复制 object file 中的某个 section
-S: Do not copy relocation and symbol information from the source file.  Also deletes debug sections.<br>
-j: Copy only the indicated sections from the input file to the output file.
```shell
# Display the full contents of any sections requested
objcopy -S -j .text -O binary %s.o %s.dl
```
