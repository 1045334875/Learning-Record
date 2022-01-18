# S特权级寄存器

> [RISC-V特权级寄存器及指令文档_Pandacooker的博客-CSDN博客_mcause寄存器](https://blog.csdn.net/Pandacooker/article/details/116423306)

### 1. Sstatus

XLEN-bit read/write register

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210508210527469.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1BhbmRhY29va2Vy,size_16,color_FFFFFF,t_70)

**位说明**：
（1）**SPP**表明进入S态之前的模式：当之前为user模式，则为0，其他为1
（2）**SIE**使能S态的全局中断。为0时S态的中断不发生；当运行在U态，SIE中的值被忽略，S态中断使能总被允许；可以通过sie寄存器关闭S态的独立中断源
（3）**SPIE**记录进入S态之前的中断使能情况
（4）**UIE**使能U模式的中断：U模式中断使能当且仅当UIE置位且hart运行在U模式
（5）**UPIE**表明在处理u模式trap前，u模式中断是否使能；当一个URET指令被执行时，UIE被设置为UPIE，且UPIE设置为1。用户级中断是可选的。如果省略，表示UIE和UPIE位固定为零
（6）**PUM**(Protect User Memory) 修改s模式加载、存储和取指令访问虚拟内存的权限.

PUM机制可以防止管理软件无意中访问用户内存。
当**PUM=0**时，翻译和保护行为正常。当**PUM=1**时，s模式内存访问U模式可访问的页面将故障。在u模式下执行PUM不起作用。

sstatus寄存器是mstatus寄存器的子集。在一个简单的实现中，读取或写入sstatus中的任何字段等同于读取或写入mstatus中的同名字段。

### 2. stvec寄存器

XLEN-bit read/write register
**功能**：
保存s模式的trap向量基址。stvec总是4字节对齐

**寄存器结构**：![在这里插入图片描述](https://img-blog.csdnimg.cn/20210508210550431.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1BhbmRhY29va2Vy,size_16,color_FFFFFF,t_70)

**3. Sip sie寄存器**

XLEN-bit read/write register

**寄存器结构**：![在这里插入图片描述](https://img-blog.csdnimg.cn/20210508210556717.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1BhbmRhY29va2Vy,size_16,color_FFFFFF,t_70)

sip寄存器是一个**xlen位**的**读/写寄存器**，包含关于挂起中断的信息。sip寄存器中除了SSIP和USIP之外的所有位都是只读的
而sie是对应的包含中断使能位的xlen位读/写寄存器。

### 4. Supervisor Timers and Performance Counters

S态软件使用相同的硬件性能监控设施作为用户模式软件，
包括时间、周期和插入csr。SBI应该提供一种修改机制
计数器的值。
SBI必须提供一种根据实时计数器来调度计时器中断的工具time

### 5. Sscratch Supervisor Scratch Register XLEN-bit read/write register

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210508210607609.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1BhbmRhY29va2Vy,size_16,color_FFFFFF,t_70)

通常，当hart执行用户代码时，sscratch用于保存指向hart-local supervisor上下文的指针。在trap处理程序的开头，sscratch与用户寄存器交换，以提供初始工作寄存器。

### 6. Sepc [ S态程序异常计数器 ] XLEN-bit read/write register

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210508210613796.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1BhbmRhY29va2Vy,size_16,color_FFFFFF,t_70)
**功能**：
sepc的低位
(sepc[0])总是零。不支持指令集扩展的实现
16位指令对齐时，两个低位(sepc[1:0])总是零。
当trap被捕获时，sepc被写入遇到异常的指令的虚拟地址