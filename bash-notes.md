### [Piping both stdout and stderr](https://stackoverflow.com/questions/16497317/piping-both-stdout-and-stderr-in-bash)
grep -i: case insensitive
```shell
cmd-doesnt-respect-difference-between-stdout-and-stderr |& grep -i SomeError
```
`|&` 相当于 `2>&1 |`，使 stderr 也重定向到 stdout 而不向终端输出。 参见 [pipeline 原理](https://stackoverflow.com/questions/9834086/what-is-a-simple-explanation-for-how-pipes-work-in-bash#answer-63979785)。

### 如何提取出待匹配字符周围的字符
```-o, --only-matching       show only nonempty parts of lines that match```\
`-P, --perl-regexp         PATTERNS are Perl regular expressions`\
`-E --extended-regexp         Interpret PATTERNS as Perl-compatible regular expressions (PCREs).`\
grep 的 -o 选项可以只显示匹配的 pattern，而 pattern 又是一个正则表达式，所以我们只需在待匹配字符的前后加上若干数量的通配符即可。比如我想显示 “write” 周围前后 10 个字符（如果存在的话），那 pattern 应写作 `"grep -o .\{0,10\}write.\{0,10\}"` `grep -o -P".{0,10}write.{0,10}"`

