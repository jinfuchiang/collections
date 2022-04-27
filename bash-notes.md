### [Piping both stdout and stderr](https://stackoverflow.com/questions/16497317/piping-both-stdout-and-stderr-in-bash)
grep -i: case insensitive
```shell
cmd-doesnt-respect-difference-between-stdout-and-stderr |& grep -i SomeError
```
有时不这样用grep不到想要的结果
