### 为什么条件变量的wait操作需要传一个锁（为什么不让程序员自己实现上锁和解锁）
- [Ref](https://stackoverflow.com/a/46937081)
- 正确使用条件变量必须使用锁
- 让程序员在wait外上锁和解锁会增加上下文切换次数。而操作系统的wait可以实现，当锁被其他线程持有时，直接将线程从条件变量队列移动到互斥锁队列，而无需上下文切换。
### toread
- [条件变量在临界区外notify会导致优先级翻转](https://groups.google.com/g/comp.programming.threads/c/wEUgPq541v8/m/ZByyyS8acqMJ)
