#### 技法：两次 fork() 的应用场景
两次 fork() 是指父进程 fork() 一次，子进程再 fork() 一次，之后子进程exit()，孙子进程变 orphan（daemon）。
1. 减少父进程阻塞时间（防止僵尸进程）
- 此场景下，父进程一般很忙，fork()子进程后不能允许长时间 wait()。两次 fork() 把任务转交给孙子进程，使子进程得以很快 exit()，减少父进程阻塞在 wait() 的时间。 而孙子进程会在子进程 exit() 后认 init 为父进程，所以孙子进程退出后不会变成僵尸进程。
2. shell开daemon进程
- 理论上，只要父进程比子进程先 exit，子进程就变成 daemon 进程了
- 但 shell 因为会长期运行，一般不会 exit，所以只有通过两次 fork() 开 daemon 进程

#### 进程
[理解Linux进程](https://tobegit3hub1.gitbooks.io/understanding-linux-processes/content/)

#### 引发 SEGFAULT 的原因
[执行与特权级不匹配的指令也会引起SEGFAULT](https://stackoverflow.com/questions/22292963/is-there-a-list-of-errors-will-show-up-as-segfaults-when-they-are-not-really-r)
