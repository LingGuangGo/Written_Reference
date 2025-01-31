##  Linux的多任务, 多进程, 多线程

1. 多任务的定义:
   + OS需要处理的事件;

### 进行和线程的区别

1. 进程和线程: 执行任务的方法;

| 区别         | 进程                       | 线程                                     |
| ------------ | -------------------------- | ---------------------------------------- |
| 主要区别     | 资源分配的最小单位         | 程序执行的最小单位<br />OS的最小调度单位 |
| 组成         | 拥有多个线程               | 共享地址空间, 访问相同的数据             |
| 可执行       | 程序执行时的一个实例(大)   | 线程是进程的一个执行流(小)               |
| 保存状态信息 | PCB                        | TCB Thread control block                 |
| 页表         | 地址空间改变, 切换当前页表 | 地址空间不变, 不用切换页表               |
| 内存空间     | 完全的内存空间             | **独立**堆栈和局部变量; 内存共享         |
| 影响         | 进程间不影响               | 一个线程死掉就等于**整个**进程死掉       |

### 基本描述

1. 进程描述	
   + 进程是程序执行时的一个实例;
   + 进程的目的就是担当分配系统资源（CPU时间、内存等）的基本单位;
2. 进程的创建和执行
   + 进程的创建 :
     + 必须分配给它独立的地址空间，
     + 建立众多的数据表来维护它的代码段、堆栈段和数据段
3. 线程的描述
   + 线程是进程的一个执行流，是CPU调度和分派的基本单位，
   + 它是比进程更小的能独立运行的基本单位;

###  使用多线程原因

1. 原因一: 和进程相比，它是一种非常"节俭"的多任务操作方式.
   + 进程创建 :  花费较多的时间维护其内存空间
   + 线程创建:  只需要在执行的时候, 分配栈空间和局部变量空间就行;
2. 原因二: 和进程相比，线程间方便的通信机制
   + 进程间: 数据的传递只能通过**通信**的方式进行;
   + 线程间: 同步和互斥机制就能实现;
3. 原因三: 
   + 多线程程序作为一种多任务、并发的工作方式
   + 多线程技术: 将耗时长的操作（time consuming）单独置于一个新的线程;
   + OS **使得线程数不大于CPU数目时，不同的线程运行于不同的CPU上**。