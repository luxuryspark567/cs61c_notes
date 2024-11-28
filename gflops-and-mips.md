# GFLOPS & MIPS

* **Use GFLOPS** when evaluating systems that are heavily dependent on **floating-point operations**, like scientific computing, AI, or graphics.
* **Use MIPS** for general-purpose processors, especially in embedded systems and microcontrollers that perform fixed-point or integer-heavy tasks.
* **For fixed-point MCUs**, **MIPS** or other embedded-specific benchmarks (like **Dhrystone** or **CoreMark**) are more appropriate than GFLOPS.

## MIPS

**MIPS** (Million Instructions Per Second) 是衡量 CPU 性能的一种指标，表示处理器每秒能够执行的指令数量（以百万为单位）。MIPS 主要用于表示 CPU 执行指令的速度，但它不考虑指令的复杂性或内存访问延迟。

#### **MIPS 计算公式**：

$$
MIPS= 
\frac{Time Taken (in seconds)} {
Number of Instructions Executed (in millions)}
$$

或者更常见的计算方式是使用 CPU 的 **时钟周期数（Clock Cycles）** 和 **每个指令执行的周期数（CPI）**：

$$
MIPS= 
\frac{Clock Speed (in Hz)}{CPI×10^6}
$$

#### 关键参数说明：

1. **Clock Speed (时钟频率)**：通常以赫兹（Hz）为单位，表示 CPU 每秒钟执行的时钟周期数。常见单位是 GHz（吉赫兹），即 10910^9109 Hz。
2. **CPI (Cycles Per Instruction)**：每个指令平均需要多少个时钟周期才能完成。CPI 受 CPU 架构、指令类型和内存访问等因素的影响。例如，某些复杂指令可能需要多个时钟周期，而简单的加法指令可能只需要一个时钟周期。
3. **Number of Instructions Executed**：计算执行的指令总数，通常以百万（10610^6106）为单位。
4. **Time Taken**：计算程序或任务运行的总时间，通常以秒为单位。

#### **计算过程举例**：

假设一个 CPU 的时钟频率为 2 GHz（即 2×1092 \times 10^92×109 Hz），每条指令的平均执行时间为 1 个时钟周期（即 CPI = 1）。

根据公式, 代入数据：

$$
MIPS= 
\frac{2 \times 10^9Hz}{1 \times 10^6}=2000MIPS
$$

因此，**MIPS** = 2000，表示该 CPU 每秒可以执行 2000 百万条指令。

#### **影响 MIPS 的因素**：

* **CPI**：更高的 CPI 意味着每条指令需要更多的时钟周期来执行，这将导致 MIPS 值下降。例如，复杂的浮点操作或内存访问可能需要更高的 CPI。
* **时钟频率**：更高的时钟频率可以提高每秒的时钟周期数，因此提升 MIPS 性能。然而，随着时钟频率的增加，热量和功耗也会增加，最终受到物理和技术限制。

#### **总结**：

* **MIPS** 是衡量 CPU 指令吞吐量的一个指标，特别适用于评估基于简单、固定任务的处理器性能。
* 计算 **MIPS** 需要知道 CPU 的时钟频率（Clock Speed）和每条指令的平均时钟周期数（CPI）。
* 然而，MIPS 并没有考虑指令复杂性、内存延迟和其他性能瓶颈，因此不能完全反映真实的处理能力，尤其是在处理复杂任务时。

## GFLOPS

To calculate the theoretical **GFLOPS** (Giga Floating Point Operations per Second) of a CPU, you need to consider the following key factors:

1. **Clock Speed (in GHz)**: The number of cycles the CPU executes per second.
2. **Number of Cores**: The total number of processing units (cores) in the CPU.
3. **Instructions Per Cycle (IPC)**: The number of instructions the CPU can execute per clock cycle. For floating-point operations, you specifically need to know how many floating-point operations each core can perform per cycle.
4. **Floating Point Operations Per Instruction (FLOP per Instruction)**: How many floating-point operations each instruction executes. This typically depends on the CPU's architecture (e.g., scalar, superscalar, SIMD).

#### Formula for Theoretical GFLOPS

$$
Theoretical \, GFLOPS=Number \, of \, Cores \times Clock\,Speed(GHz) \times IPC \times FLOP \, per \, Instruction
$$



#### Steps:

1. **Clock Speed**: Typically given in GHz (gigahertz), which is 10910^9109 cycles per second.
2. **Number of Cores**: The number of physical cores in the CPU. For multi-core processors, this is usually specified (e.g., a 4-core or 8-core processor).
3. **IPC (Instructions Per Cycle)**: This value is highly dependent on the CPU's architecture. Modern CPUs can execute multiple instructions per cycle, and this number may vary under different workloads. For simplicity, you can assume the typical value based on the CPU's architecture or consult the manufacturer specifications.
4. **FLOP per Instruction**: The number of floating-point operations executed per instruction. For example, some architectures might execute one or more floating-point operations (like adding or multiplying multiple floating-point numbers in one instruction). For a simple case, you might assume **1 FLOP per instruction**, but it could be higher in vectorized operations (like SIMD) or specialized floating-point units.

#### Example Calculation:

Let's assume a CPU has the following characteristics:

* **Clock Speed**: 3.0 GHz
* **Number of Cores**: 4 cores
* **IPC**: 4 (meaning the CPU can issue 4 instructions per clock cycle, typically under optimal conditions)
* **FLOP per Instruction**: 2 (assuming each instruction can perform 2 floating-point operations, such as a SIMD instruction)

Now, using the formula:

$$
Theoretical GFLOPS=4(cores)×3.0(GHz)×4(IPC)×2(FLOP per Instruction)
$$

$$
Theoretical GFLOPS=4×3.0×4×2=96GFLOPS
$$

So, the theoretical performance of this CPU is **96 GFLOPS**.

#### Notes:

* **Real-world performance** <mark style="color:yellow;">will usually be lower</mark> than theoretical performance <mark style="color:yellow;">due to inefficiencies like memory latency, cache misses, or non-ideal instruction pipelines.</mark>
* **FLOP per Instruction** <mark style="color:yellow;">can be higher in CPUs with SIMD (Single Instruction, Multiple Data) or AVX (Advanced Vector Extensions) support, which can perform multiple floating-point operations per instruction.</mark>
* **IPC** varies with workload and CPU architecture, and it <mark style="color:yellow;">can be lower</mark> than the maximum theoretical IPC due to <mark style="color:yellow;">pipeline stalls, data dependencies, or other limitations in practical execution.</mark>

