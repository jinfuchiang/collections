## git restore
- restore file from **the index** to working tree
```shell
git restore [--worktree] <filename>
```
- restore file from **HEAD** to the index
```shell
git restore --staged <filename> # same as using git reset
```
- restore file from **a given commit** (can be combined with --staged and --worktree)
```shell
git restore --source
```
