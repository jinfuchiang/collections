### 利用 CUDA 实现 find_repeat
- find_reapeat: Given an array of integers `device_input`, returns an array of all indices `i` for which `device_input[i] == device_input[i+1]`. Returns the total number of pairs found.
- input: [2, 2, 3, 8, 1, 1, 5, 0, 0]
- output:[0, 4, 7]
- 难点在于，如何无锁、并行地写入结果
- 解决思路是，预计算出重复元素的索引在结果数组的坐标（索引）
- 实现：input: [2, 2, 3, 8, 1, 1, 5, 0, 0] -> indicator: [1, 0, 0, 0, 1, 0, 0, 1, 0] -> exclusive_prefix_sum: [0, 1, 1, 1, 1, 2, 2, 2, 3] -> output:[0, 4, 7]
```cpp
__global__ void gather_kernel(int* exclusive_prefix_sum, int* output, const int N, int* total_count) {
    unsigned int idx {blockIdx.x * blockDim.x + threadIdx.x};
    if (idx < N - 1) {
        // 如果
        if (exclusive_prefix_sum[idx] != exclusive_prefix_sum[idx + 1]) {
            output[exclusive_prefix_sum[idx]] = idx;
        }
    } else if (idx == N - 1) {
        *total_count = exclusive_scan_results[N - 1];
    }
}
```
### 什么是 SIMT
- single instruction, multiple threads
- 一个GPU包含多个SM，每个SM有多个 core，每个核跑 1 个线程。比如：Fermi（费米）GPU有 16 个 SM，每个 SM 有32个 core，所以最多运行 512 个线程
- 一个时钟周期内，相同 SM 内的 cores 执行相同的指令。也就是多个线程执行同一条指令（SIMT）

### SIMD v.s SIMT
REF:[SIMD < SIMT < SMT: parallelism in NVIDIA GPUs](https://yosefk.com/blog/simd-simt-smt-parallelism-in-nvidia-gpus.html)
```C
void add(uint32_t *a, uint32_t *b, uint32_t *c, int n) {
  for(int i=0; i<n; i++) c[i] = a[i] + b[i];
}
```
#### SIMD 写法
```C
void add(uint32_t *a, uint32_t *b, uint32_t *c, int n) {
  for(int i=0; i<n; i+=4) {
    uint32x4_t a4 = vld1q_u32(a+i);
    uint32x4_t b4 = vld1q_u32(b+i);
    uint32x4_t c4 = vaddq_u32(a4,b4);
    vst1q_u32(c+i,c4);
  }
}
```
#### SIMT 写法(aka CUDA写法)
```C
__global__ void add(float *a, float *b, float *c, int n) {
    int i = blockIdx.x * blockDim.x + threadIdx.x;
    if(i < n)
        a[i]=b[i]+c[i]; //no loop!
}
```
