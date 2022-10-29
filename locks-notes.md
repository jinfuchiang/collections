## 如何评价锁
- 开销（overhead）
- 公平性（fairness）
## 自旋锁（Spin lock）
### 实现方式
- Test-And-Set（我更喜欢说Set-And-Test）：原子的写并返回旧值
- Compare-And-Swap：与原值相等则写新值返回True，否则不写返回False
- 维护一个变量，为 0 代表该锁空闲，为 1 代表锁忙碌
### 评价
- 开销： 竞争激烈（high contention）的情况下，CPU 浪费在自旋上（忙等、轮询）
- 公平性：一般，无法保证线程一定不饥饿
## 排号自旋锁（Ticket lock）
### 实现方式
- Fetch-And-Add：原子加一并返回旧值
- 维护两个变量，ticket 记录下一个号码，turn 记录可服务或正在服务的号码
### 评价
- 开销：与自旋锁相似
- 公平性：很公平
