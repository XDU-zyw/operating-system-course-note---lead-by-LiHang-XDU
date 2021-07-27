[TOC]
<font face = "Consolas">

# 1 调度(Scheduling)
> 所有进程之间的关系
(多进程就绪时,哪一个应该在CPU上执行)
何时调度 怎么调度 怎么适合上层应用

## 1.1 何时调度
* 进程生成(process create)
* 进程退出(process exits)
    * 此进程放弃CPU,决定下一个进程进入
* 进程因IO堵塞(process block by IO)
* IO中断(IO interrupt)
    * IO等待的包到达后唤醒堵塞进程转变为就绪态

## 1.2 怎么调度
> 即调度算法(操作系统的**核心**)

课本分类(不严格):
****
### 1.2.1 抢占和非抢占(Preemptive & Non-Preemptive)
* 抢占:高优先级进程可能抢占正在运行进程的CPU资源
    > 问题:可能优先级反转,死锁 
        >优先级反转问题:有优先级时高优先级进程就绪会使得在临界区中的低优先级进程无法被调度,就无法离开临界区
### 1.2.2 批处理调度(Batch Scheduling)
> 一次性运行多个进程(提高吞吐量,减少结束间隔(turnaround time),提高CPU利用率)
尽量提高硬件利用率
#### 1.2.2.1 各时间定义
> **burst time**: 执行时间
> **throughout**: 单位时间完成进程数
> **turnaround time**: 响应到结束的间隔
> **waiting time**: 进程在就绪队列等待的时间
> **response time**: 从提交到进程第一次响应的间隔
#### 1.2.2.2 SJF(Short-Job-First)
> 选择剩余执行时间最短的进程执行(一般不可知执行时间)
****
### 1.2.3 交互系统调度(Interactive System Scheduling)
> 与外部系统发生交互(人机交互 计算机间交互 外设计算机交互)
通常希望外部事件来时可立刻响应 --> 一般新进程优先级较高
#### 1.2.3.1 Round-Robin Scheduling
> 每个进程分配等长的时间片,循环进行(完成后放弃剩余时间)
一般用于实时系统,在Linux中实现
#### 1.2.3.2 基于优先级调度(Priority Scheduling)
> 每次选择最高优先级的进程调度
(Multiple Queue)每个优先级队列有自己的独立的调度算法
可能饿死进程(starvation)
#### 1.2.3.3 保证式调度(Guaranteed Scheduling)
> 确保就绪态进程某种程度的运行 --> (如用于云服务器承诺的配置)
#### 1.2.3.4 随机调度(Lottery Scheduling)
#### 1.2.3.5 FSS(Fair-Share Scheduling)
> 每个用户使用同样的CPU时间(无论每个用户进程的多少) --> Guaranteed Scheduling的特例
****
### 1.2.4 实时调度(Real Time Scheduling)
> 某个时限内完成
硬实时(Hard Real-Time): 计算必须在特定时限内完成
软实时(Soft Real-Time): 尽量实现,超过时限可接受 --> (如视频加载)
可调度性(Scheduling): 调度算法能否找到方法确保各个进程在时限前完成
****
## 1.3 调度实现和目标策略分开(Policy Versus Mechanism)
> 提供多种调度算法,用户指定调度算法(目标策略),操作系统选择符合的实现机制
****
## 1.4 Thread Scheduling
> 用户态调度(可指定线程调度器)或内核态调度(开销大)