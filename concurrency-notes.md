## 并发问题两大竞争
### 数据竞争（data race）
- 原子性：锁
### 控制流竞争（control race）
- 代码执行顺序：条件变量、信号量

## 如何评价锁
- 开销（overhead）
- 公平性（fairness）
## 自旋锁（Spin lock）
### 实现方式
- Test-And-Set（我更喜欢说Set-And-Test）：原子的写并返回旧值（eg. xchg rax, [rbx]）
- Compare-And-Swap：与原值相等则写新值返回True，否则不写返回False
- 维护一个变量，为 0 代表该锁空闲，为 1 代表锁忙碌
### 评价
- 开销： 
1. 竞争激烈（high contention）的情况下，CPU 浪费在自旋上（忙等、轮询）
2. 使用 Test-And-Set 实现的锁，会因为写操作使 cache 频繁失效而导致性能低下
- 公平性：一般，无法保证线程一定不饥饿

## 排号自旋锁（Ticket lock）
### 实现方式
- Fetch-And-Add：原子加一并返回旧值
- 维护两个变量，ticket 记录下一个号码，turn 记录可服务或正在服务的号码
### 评价
- 开销：与自旋锁相似，但没有 cache 频繁失效的问题
- 公平性：FIFO 式公平

### yield()、 sleep() 和 sched() 区别
- yield() 和 sched() ：Running->Runable(or Ready)
- sleep() ：Running->Blocked

### 为什么条件变量的wait操作需要传一个锁（为什么不让程序员自己实现上锁和解锁）
- [Ref](https://stackoverflow.com/a/46937081)
- 正确使用条件变量必须使用锁
- 让程序员在wait外上锁和解锁会增加上下文切换次数。而操作系统的wait可以实现，当锁被其他线程持有时，直接将线程从条件变量队列移动到互斥锁队列，而无需上下文切换。
### toread
- [条件变量在临界区外notify会导致优先级翻转](https://groups.google.com/g/comp.programming.threads/c/wEUgPq541v8/m/ZByyyS8acqMJ)
