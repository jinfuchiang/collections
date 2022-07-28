### [Kqueue: A generic and scalable event notification facility](https://people.freebsd.org/~jlemon/papers/kqueue.pdf)笔记
#### poll() 和 select() 缺陷
1. 无状态的 poll() 和 select() 导致的不可扩展性（Not scalable）
    <br>无状态：内核自身不保存应用程序感兴趣的 fd，具体表现如下：
    1. 每次调用返回都需跨内核/用户拷贝**所有**被监控的文件描述符。然而实践表明，每次调用返回的活动 fd 只占 5%。
    2. 应用程序需要 O(N) 的时间遍历 fd list，找到所有活动 fd
    3. 内核需要专门为 fd list 开辟空间，然后做拷贝，还要在函数返回时释放空间。
    4. 内核也需要 O(N) 的时间遍历 fd list，找到活动的 fd
2. poll() 和 select() 能监控 fd 有限
    1. select 使用定长 bitmap 作为 fd list 的参数类型，上限是 FD_SETSIZE(1024)
    2. poll 使用动态数组作为 fd list 的参数类型，上限是系统文件描述的上限
#### level-triggered v.s edge-triggered
1. 水平触发是指，如果满足某个条件则触发该事件，如果条件一直满足则事件一直会被触发
2. 边沿触发是指，只有在第一次检测到条件满足时才会触发事件
#### epoll原理
1. epoll() 在内核内采用红黑树维护应用程序感兴趣的 fd。应用通过epoll_ctl()向红黑树增加 fd，而不必每次传所有的 fd，解决了缺陷1.1。
2. epoll()内部维护一个活动 fd 的链表。epoll_wait() 时该链表，链表内所有 fd 都是有活动的，应用程序无需再遍历一次，解决了缺陷1.4。
