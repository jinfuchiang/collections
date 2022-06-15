## 隐蔽信道
### 访存周期级测时
```C
/*
 * Loads from virtual address addr and measure the access time
 */
CYCLES measure_one_block_access_time(ADDR_PTR addr)
{
    CYCLES cycles;

    asm volatile("mov %1, %%r8\n\t"
            "lfence\n\t"
            "rdtsc\n\t"
            "mov %%eax, %%edi\n\t"
            "mov (%%r8), %%r8\n\t"
            "lfence\n\t"
            "rdtsc\n\t"
            "sub %%edi, %%eax\n\t"
    : "=a"(cycles) /*output*/
    : "r"(addr)
    : "r8", "edi");

    return cycles;
}
```
### x86 读取周期级时钟
```C
/* 
 * Returns Time Stamp Counter 
 */
extern inline __attribute__((always_inline))
CYCLES rdtscp(void) {
	CYCLES cycles;
	asm volatile ("rdtscp"
	: /* outputs */ "=a" (cycles));

	return cycles;
}
/* 
 * Gets the value Time Stamp Counter 
 */
inline CYCLES get_time() {
    return rdtscp();
}
```
### 收发双方如何同步时间
误差小于CHANNEL_SYNC_JITTER，或大于CHANNEL_SYNC_TIMEMASK
```C
/* Synchronizes at the overflow of a counter
 *
 * Counter is created by masking the lower bits of the Time Stamp Counter
 * Sync done by spinning until the counter is less than CHANNEL_SYNC_JITTER
 */
#define CHANNEL_SYNC_TIMEMASK           0x000FFFFF
#define CHANNEL_SYNC_JITTER             0x0100
extern inline __attribute__((always_inline))
CYCLES cc_sync() {
    while((get_time() & CHANNEL_SYNC_TIMEMASK) > CHANNEL_SYNC_JITTER) {}
    return get_time();
}
```
## Shell
### 公私钥 for ssh
```shell
ssh-keygen -t ed25519 -C "jinfuchiang@outlook.com"
# Copies the contents of the id_ed25519.pub file to your clipboard
clip < ~/.ssh/id_ed25519.pub
# 将粘贴板的内容追加至服务器的~/.ssh/authorized_key文件
```
### pacman包升级操作
- 更新包数据库后应立即更新所有已安装的包
- 原因：<a href = "https://wiki.archlinux.org/title/System_maintenance#Partial_upgrades_are_unsupported">Arch不支持部分更新包</a>
- 使用下述命令确保总能安全地升级
```shell
# S表示sync y表示部分更新包数据库
# yy代表全面更新包数据库 u代表更新所有已安装的包
# 加packages表示安装包
pacman -Syu [packages]
pacman -Syyu [packages]
# never do: pacman -Sy && pacman -S [packages]
```
## Arm
### Cycle clcok
#### ARMv7-A 
```C
#if (__ARM_ARCH >= 6)  // V6 is the earliest arch that has a standard cyclecount
  uint32_t pmccntr;
  uint32_t pmuseren;
  uint32_t pmcntenset;
  // Read the user mode perf monitor counter access permissions.
  asm volatile("mrc p15, 0, %0, c9, c14, 0" : "=r"(pmuseren));
  if (pmuseren & 1) {  // Allows reading perfmon counters for user mode code.
    asm volatile("mrc p15, 0, %0, c9, c12, 1" : "=r"(pmcntenset));
    if (pmcntenset & 0x80000000ul) {  // Is it counting?
      asm volatile("mrc p15, 0, %0, c9, c13, 0" : "=r"(pmccntr));
      // The counter is set up to count every 64th cycle
      return static_cast<int64_t>(pmccntr) * 64;  // Should optimize to << 6
    }
  }
#endif
```
[Referrence](https://github.com/google/benchmark/blob/b3c08f6ec39b9bfe4ec2ba45d1726582eea096a8/src/cycleclock.h)
#### AArch64
```C
  uint64_t pmccntr;
  uint64_t pmuseren;
  uint64_t pmcntenset;
  // Read the user mode perf monitor counter access permissions.
  asm volatile("mrs %0, pmuserenr_el0" :"=r"(pmuseren));
  if (pmuseren & 1) {  // Allows reading perfmon counters for user mode code.
    asm volatile("mrs %0, pmcntenset_el0" :"=r"(pmcntenset));
    if (pmcntenset & 0x80000000ul) {  // Is it counting?
      asm volatile("mrs %0, pmcntenset_el0" :"=r"(pmccntr));
      // The counter is set up to count every 64th cycle
      return static_cast<int64_t>(pmccntr) * 64;  // Should optimize to << 6
    }
  }
```
