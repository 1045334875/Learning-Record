# Homework 3

#### 1. Operating System Concepts Chapter 1 Exercises: 1.14, 1.17, 1.19, 1.22 (20 points)

###### 1.14 What is the purpose of interrupts? How does an interrupt differ from a trap? Can traps be generated intentionally by a user program? If so, for what purpose?

The purpose of interrupts throughout modern operating systems is to handle asynchronous events.

Differences:

1. The trap is a signal raised by a user program instructing the operating system to perform some functionality immediately. In contrast, the interrupt is a signal to the CPU emitted by hardware that indicates an event that requires immediate attention.
2. A trap also triggers OS functionality. It gives control to the trap handler. In contrast, an interrupt triggers the CPU to perform the interrupt handler routine.
3. A trap is synchronous and may occur after the execution of the instruction. In contrast, an interrupt is asynchronous and may occur at any time.
4. A trap is generated by a user program instruction. In contrast, the hardware devices generate an interrupt.

Yes, traps can be generated by a user program for instructing the operating system to do some instruction.

###### 1.17 Some computer systems do not provide a privileged mode of operation in hardware. Is it possible to construct a secure operating system for these computer systems? Give arguments both that it is and that it is not possible.

If it is possible:

We can fix some system functions on the hardware and can't be rewritten. The security of the system depends on security of each application. If the programming languages are safe in memory space processing, it's possible to construct a secure operating system.

If it is not possible:

We can't promise all the applications are safe. If there isn't a privileged mode,  malicious programs will rewrite the operating system code and may damage some vital functions of the operating system. 

###### 1.19 Rank the following storage systems from slowest to fastest: 

###### a. Hard-disk drives b. Registers c. Optical disk d. Main memory e. Nonvolatile memory f. Magnetic tapes g. Cache

1. f. Magnetic tapes
2. c. Optical disk
3. a. Hard-disk drive
4. e. Nonvolatile memory
5. d. Main memory
6. g. Cache
7. b. Registers

###### 1.22 Describe a mechanism for enforcing memory protection in order to prevent a program from modifying the memory associated with other programs

Virtual memory can be used as a memory protection tool, which stores the permissions and memory addresses of each process. Kernel and user modes are set in the operating system. The system checks the mode of each process before executing the instruction. When a process attempts to perform some operations beyond its mode, it will trigger the system exception function.

#### 2. Detail your steps about how to get arch/arm64/kernel/sys.i (10 points)

```
 //?????????????????????????????????
 $docker start oslab1  //???????????????????????????oslab1
 $docker ps  //?????????????????????????????????????????????????????????????????????????????????
 $docker exec -it oslab1 bash   //???????????????docker??????(oslab1)
 root@(?????????):/# 
```

![image-20211121002852613](C:\Users\86181\Desktop\image-20211121002852613.png)

????????????????????????????????????arm???????????????aarch tool chain????????????????????????

**???linux-5.15???????????????**??????????????????????????????

```
 #apt-get update
#apt-get install gcc-aarch64-linux-gnu
#aarch64-linux-gnu-gcc -v //??????gcc??????????????????????????????????????????????????????
#make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- defconfig//????????????
/*???????????????
***Default configuration is based on 'defconfig'
#
# configuration written to .config
#
???????????????*/

#apt-get install libssl-dev
#make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- arch/arm64/kernel/sys.i -j $(nproc) //?????? 
//nproc????????????,?????????????????????????????????????????????????????????????????????????????????????????? -j ???????????????????????? (out of memory)???????????????????????????c'd????????? -j4, -j8 ??????
```

#### 3. Find system call table of Linux v5.15 for ARM32, RISC-V(32 bit), RISC-V(64 bit), x86(32 bit), x86_64 (50 points)

List source code file, the whole system call table with macro expanded, screenshot every step.

```
??????oslab1?????????linux-5.15?????????
#find / -name 'syscall*' //????????????*???????????????
```

![image-20211125131628882](C:\Users\86181\Desktop\image-20211125131628882.png)

??????????????????????????????????????????syscall?????????????????????166????????????????????????????????????????????????

```
- /have-fun-debugging/linux-5.15/arch/riscv/kernel/syscall_table.c
- /have-fun-debugging/linux-5.15/arch/x86/entry/syscalls/syscall_64.tbl
- /have-fun-debugging/linux-5.15/arch/x86/entry/syscalls/syscall_32.tbl
- /have-fun-debugging/linux-5.15/arch/arm/tools/syscall.tbl
```

.tbl??????????????????terminal?????????cat????????????????????????????????????????????????system call table???.c????????????????????????????????????????????????????????????

- /have-fun-debugging/linux-5.15/arch/arm/tools/syscall.tbl

<img src="C:\Users\86181\Desktop\image-20211125133141452.png" alt="image-20211125133141452" style="zoom:67%;" />

<img src="C:\Users\86181\Desktop\image-20211125133205830.png" alt="image-20211125133205830" style="zoom:67%;" />

<img src="C:\Users\86181\Desktop\image-20211125133257554.png" alt="image-20211125133257554" style="zoom:67%;" />

- /have-fun-debugging/linux-5.15/arch/x86/entry/syscalls/syscall_32.tbl

<img src="C:\Users\86181\Desktop\image-20211125133416865.png" alt="image-20211125133416865" style="zoom:67%;" />

<img src="C:\Users\86181\Desktop\image-20211125133444863.png" alt="image-20211125133444863" style="zoom:67%;" />

<img src="C:\Users\86181\Desktop\image-20211125133512085.png" alt="image-20211125133512085" style="zoom:67%;" />

??????448????????????????????????

- /have-fun-debugging/linux-5.15/arch/x86/entry/syscalls/syscall_64.tbl

  <img src="C:\Users\86181\Desktop\image-20211125133708068.png" alt="image-20211125133708068" style="zoom:67%;" />

  <img src="C:\Users\86181\Desktop\image-20211125133835218.png" alt="image-20211125133835218" style="zoom:67%;" />

  <img src="C:\Users\86181\Desktop\image-20211125133851551.png" alt="image-20211125133851551" style="zoom:67%;" />

  ??????547?????????????????????

- /have-fun-debugging/linux-5.15/arch/riscv/kernel/syscall_table.c

???riscv??????????????????????????????syscall_table.c??????????????????????????????????????????64??????32???????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????64???riscv64-unknown-linux-gnu-gcc??????????????????????????????

```
#make ARCH=riscv CROSS_COMPILE=riscv64-unknown-linux-gnu- arch/riscv/kernel/syscall_table.i -j$(nproc)
????????????????????????.i??????.c????????????????????????
```

<img src="C:\Users\86181\Desktop\image-20211125151007027.png" alt="image-20211125151007027" style="zoom:67%;" />

<img src="C:\Users\86181\Desktop\image-20211125151846487.png" alt="image-20211125151846487" style="zoom:67%;" />

#### 4.Explain what is ELF file? Try readelf and objdump command on an ELF file, give screenshot of the output.

**Run an ELF file and cat /proc/PID/maps to give its memory layout.** 

Executable and Linkable Format. It is a common standard file format for executable files, object code, shared libraries, and core dumps.

```
#touch test.c  //??????test.c
#vi test.c  //????????????test.c
Esc + :exit  //????????????
#gcc test.c  //??????????????????????????????????????????a.out
#readelf -a a.out //all??????????????????????????????-h-l-S-s-r-d-V-A-I
```

##### readelf ?????????elf???????????????

- **??????-h(elfheader)?????????elf?????????????????????????????????????????????????????????????????????**
- **??????-l(programheaders)???segments?????????????????????????????????(?????????????????????)???????????????????????????????????????**
- **??????-S(sectionheaders)???sections??????????????????(?????????????????????)???????????????????????????????????????**
- ??????-a???all??????????????????????????????-h-l-S-s-r-d-V-A-I???
- ??????-g(sectiongroups)?????????????????????(?????????????????????)???
- ??????-t???section-details????????????????????????(-S???)???
- ??????-s???symbols?????????????????????????????????????????????????????????
- ??????-e???headers?????????????????????????????????:-h-l-S???
- ??????-n???notes??????note?????????????????????????????????
- ??????-r???relocs?????????????????????????????????
- ??????-u???unwind??????unwind???????????????????????????IA64ELF???unwind????????????
- ??????-d???dynamic???????????????????????????
- ??????-V???version-info???????????????????????????
- ??????-A???arch-specific??????CPU???????????????
- ??????-I???histogram??????????????????????????????bucketlist?????????????????????
- ??????-x,hex-dump=???16???????????????????????????????????????number??????????????????????????????????????????????????????????????????
- ??????-D???use-dynamic????????????????????????????????????????????????????????????????????????
- ??????-v???version??????readelf??????????????????
- ??????-H???help??????readelf??????????????????????????????

<img src="C:\Users\86181\Desktop\image-20211125141959802.png" alt="image-20211125141959802" style="zoom:67%;" />

<img src="C:\Users\86181\Desktop\image-20211125142018551.png" alt="image-20211125142018551" style="zoom:67%;" />

<img src="C:\Users\86181\Desktop\image-20211125142307935.png" alt="image-20211125142307935" style="zoom:67%;" />

?????????????????????

#### odjdump

```
objdump -d a.out //-d ?????????????????????????????????
objdump -t a.out //?????????????????????????????????
objdump -t libc.a grep -w printf //?????? printf ??? libc.a ????????????????????????
objdump -h simple.o //????????????????????????section?????????????????????
objdump -r simple.o //??????????????????
objdump -f simple.o //??????objfile??????????????????????????????????????????
objdump -s simple.o //????????????section???????????????
objdump -x simple.o //???????????????????????????
objdump -a simple.o //??????????????????????????????
```

?????????????????????

<img src="C:\Users\86181\Desktop\image-20211125143057390.png" alt="image-20211125143057390" style="zoom:67%;" />

???????????????

<img src="C:\Users\86181\Desktop\image-20211125143240808.png" alt="image-20211125143240808" style="zoom:67%;" />

#### **Run an ELF file and cat /proc/PID/maps to give its memory layout.** 

<img src="C:\Users\86181\Desktop\image-20211126172927826.png" alt="image-20211126172927826" style="zoom:67%;" />

```
#ps aux |grep pmap //????????????pid
```

??????????????????pmap???pid???3082?????????????????????????????????????????????????????????????????????????????????????????????????????????????????????/3082/maps??????????????????????????????/proc???????????????????????????????????????????????????????????????????????????????????????

<img src="C:\Users\86181\Desktop\image-20211126173639315.png" alt="image-20211126173639315" style="zoom:67%;" />

???????????????????????????????????????????????????3087???terminal??????????????????????????????????????????????????????????????????????????????????????????????????????????????????3087??????????????????????????????????????????cat /proc/3087/maps??????????????????????????????3039???????????????

??????????????????????????????????????????

- address: 0085d000-00872000 ?????????????????????????????????????????????????????????????????????
- perms:rw-p ?????????r=read, w=write, x=execute, s=shared, p=private(copy on write)
- offset: 00000000 ???????????????????????????????????????????????????
- dev: 03:08 ????????????????????????????????????
- inode: ?????????????????????0????????????????????????????????????
- name: /lib/ld-2.2.12.so ???????????????????????????

<img src="C:\Users\86181\Desktop\image-20211126174348481.png" style="zoom:67%;" />

<img src="C:\Users\86181\Desktop\image-20211126174410508.png" alt="image-20211126174410508" style="zoom:67%;" />



**2, 3, 4 need to have screenshots.** 



 