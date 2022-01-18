| 指令   | 含义                                                         | 例           |
| ------ | ------------------------------------------------------------ | ------------ |
| LUI    | 填充寄存器的高20位                                           | lui x6,0x666 |
| SW     | s store 32-bit values from the low bits of register rs2 to memory respectively.存到内存里 | sw s0,0(sp)  |
| ORI    | ANDI, ORI, XORI are logical operations that perform bitwise AND, OR, and XOR on register rs1 and the sign-extended 12-bit immediate and place the result in rd. |              |
| SLLI   | SLLI is a logical left shift (zeros are shifted into the lower bits)逻辑左移 |              |
| LI     | ![image-20210520133345402](C:\Users\86181\AppData\Roaming\Typora\typora-user-images\image-20210520133345402.png) |              |
| BLE    | ![image-20210520133700915](C:\Users\86181\AppData\Roaming\Typora\typora-user-images\image-20210520133700915.png) |              |
| sext.w | ![image-20210520133805609](C:\Users\86181\AppData\Roaming\Typora\typora-user-images\image-20210520133805609.png) |              |
| JAL    | ![image-20210520204346475](C:\Users\86181\AppData\Roaming\Typora\typora-user-images\image-20210520204346475.png) |              |
| sd     | ![image-20210521234835214](C:\Users\86181\AppData\Roaming\Typora\typora-user-images\image-20210521234835214.png) |              |

| sb   | ![image-20210521235622648](C:\Users\86181\AppData\Roaming\Typora\typora-user-images\image-20210521235622648.png) |
| ---- | ------------------------------------------------------------ |
| bne  | ![image-20210521235939342](C:\Users\86181\AppData\Roaming\Typora\typora-user-images\image-20210521235939342.png) |
| NOP  | =ADDI X0,X0,0                                                |
|      |                                                              |
|      |                                                              |
|      |                                                              |
|      |                                                              |
|      |                                                              |

汇编程序的开头是一些汇编指示符（assemble directives）。它们是汇编器的命令，具有 告诉汇编器代码和数据的位置、指定程序中使用的特定代码和数据常量等作用。图 3.9 是 RISC-V 的汇编指示符。其中图 3.6 中用到的指示符有：

 ⚫ .text：进入代码段。

 ⚫ .align 2：后续代码按 22 字节对齐。

 ⚫ .globl main：声明全局符号“main”。

 ⚫ .section .rodata：进入只读数据段 

⚫ .balign 4：数据段按 4 字节对齐。

 ⚫ .string “Hello, %s!\n”：创建空字符结尾的字符串。 

⚫ .string “world”：创建空字符结尾的字符串。

![](C:\Users\86181\AppData\Roaming\Typora\typora-user-images\image-20210506162455189.png)

#### BSS段：BSS段（bss segment）通常是指用来存放程序中未初始化的或者初始值为0的全局变量的一块内存区域。BSS是英文Block Started by Symbol的简称。BSS段属于静态内存分配。

data段：如果数据全是零，为了优化考虑，编译器把它当作bss处理。

return value在a0里

displacement = offset

| 指令    |                                                              |             |
| ------- | ------------------------------------------------------------ | ----------- |
| LW      | The LW instruction loads a 32-bit value from memory and sign-extends this to 64 bits before storing it in register rd for RV64I.把内存的值扩到64位放到寄存器里 | lw s0,0(sp) |
| 8（x2） | 8是偏移地址，x2是短地址                                      |             |
| SRAI    | 算数右移 SRAI is an arithmetic right shift                   |             |
| BEQ,BNE | Branch instructions compare two registers. BEQ and BNE take the branch if registers rs1 and rs2 are equal or unequal respectively. |             |
| addiw   | 把符号位扩展的立即数加到 x[rs1]，将结果截断为 32 位，把符号位扩展的结果写入 x[rd]。 忽略算术溢出 |             |
| mv      | mov                                                          |             |
| auipc   | auipc  ra,0x0 //ra=pc+0;把x[ra]位置加立即数                  |             |
| lbu     | ![image-20210520132445925](C:\Users\86181\AppData\Roaming\Typora\typora-user-images\image-20210520132445925.png) |             |
| bgtu    | ![image-20210520132739263](C:\Users\86181\AppData\Roaming\Typora\typora-user-images\image-20210520132739263.png) |             |

![image-20210506202615476](C:\Users\86181\AppData\Roaming\Typora\typora-user-images\image-20210506202615476.png)

![image-20210506232014535](C:\Users\86181\AppData\Roaming\Typora\typora-user-images\image-20210506232014535.png)

1byte=8bit

![image-20210518151921993](C:\Users\86181\AppData\Roaming\Typora\typora-user-images\image-20210518151921993.png)![image-20210518151953681](C:\Users\86181\AppData\Roaming\Typora\typora-user-images\image-20210518151953681.png)![image-20210518152031963](C:\Users\86181\AppData\Roaming\Typora\typora-user-images\image-20210518152031963.png)![image-20210518152058948](C:\Users\86181\AppData\Roaming\Typora\typora-user-images\image-20210518152058948.png)



11111111

[]()

源代码-s

看key里面，读取输入的key值，比较

bne比较跳转，反追

给了源码汇编码

overflow buff

看c，可以看s，spike-d可以单步调试看内存

bonus：为什么overflow成功 了却报了segfault？？？



lab8 环境配置

elf--exe

objdump反汇编-二进制转汇编

spike--运行转……仿真器，仿cpu

riscv-pk代理内核

### 看那个网站学习溢出，然后就可以读懂思路，关于汇编的部分，再说

要移到可执行文件里再操作BOF前一步

vim

对比.c找到潜在漏洞,.s构造字符串中什么，找地址之间相对关系，here一段



![image-20210513192528207](C:\Users\86181\AppData\Roaming\Typora\typora-user-images\image-20210513192528207.png)

![image-20210513192853862](C:\Users\86181\AppData\Roaming\Typora\typora-user-images\image-20210513192853862.png)

每种C和C++的实现支持对其宿主机或操作系统唯一的功能。例如，一些程序需要精确控制超出数据所在的储存空间，或着控制特定函数接受参数的方式。#pragma指示使每个编译程序在保留C和C++语言的整体兼容性时提供不同机器和操作系统特定的功能。编译指示被定义为机器或操作系统特定的，并且通常每种编译程序是不同的。

![clip_image004[4]](https://images0.cnblogs.com/blog/92071/201310/16201603-f1bb74f9fd10480e83cbf530cdabad68.png)

