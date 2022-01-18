 Find system call table of Linux v5.15 for ARM32, RISC-V(32 bit), RISC-V(64 bit), x86(32 bit), x86_64

```
进入oslab1容器的linux-5.15文件夹
$docker start oslab1
$docker exec -it oslab1 bash
#cd have-fun-debugging
#cd linux-5.15
搜索带有syscall的文件
#find / -name 'syscall*' //一定要加*不然会报错
```

然后获得了以下一系列

```
riscv-elf/riscv64-unknown-elf/include/machine/syscall.h
/riscv-elf/share/gdb/syscalls
/riscv-glibc/sysroot/usr/include/bits/syscall.h
/riscv-glibc/sysroot/usr/include/syscall.h
/riscv-glibc/sysroot/usr/include/sys/syscall.h
/riscv-glibc/share/gdb/syscalls
/usr/lib/x86_64-linux-gnu/perl/5.30.0/bits/syscall.ph
/usr/lib/x86_64-linux-gnu/perl/5.30.0/sys/syscall.ph
/usr/lib/x86_64-linux-gnu/perl/5.30.0/syscall.ph
/usr/include/syscall.h
/usr/include/x86_64-linux-gnu/bits/syscall.h
/usr/include/x86_64-linux-gnu/sys/syscall.h
/usr/aarch64-linux-gnu/include/bits/syscall.h
/usr/aarch64-linux-gnu/include/syscall.h
/usr/aarch64-linux-gnu/include/sys/syscall.h
/have-fun-debugging/linux-5.15/lib/syscall.o
/have-fun-debugging/linux-5.15/lib/syscall.c
/have-fun-debugging/linux-5.15/Documentation/userspace-api/ebpf/syscall.rst
/have-fun-debugging/linux-5.15/Documentation/powerpc/syscall64-abi.rst
/have-fun-debugging/linux-5.15/Documentation/ABI/stable/syscalls
/have-fun-debugging/linux-5.15/Documentation/admin-guide/syscall-user-dispatch.rst
/have-fun-debugging/linux-5.15/arch/arm/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/arm/tools/syscall.tbl
/have-fun-debugging/linux-5.15/arch/arm/tools/syscallnr.sh
/have-fun-debugging/linux-5.15/arch/x86/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/x86/include/asm/syscalls.h
/have-fun-debugging/linux-5.15/arch/x86/include/asm/syscall_wrapper.h
/have-fun-debugging/linux-5.15/arch/x86/um/syscalls_64.c
/have-fun-debugging/linux-5.15/arch/x86/um/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/x86/um/shared/sysdep/syscalls.h
/have-fun-debugging/linux-5.15/arch/x86/um/shared/sysdep/syscalls_64.h
/have-fun-debugging/linux-5.15/arch/x86/um/shared/sysdep/syscalls_32.h
/have-fun-debugging/linux-5.15/arch/x86/um/syscalls_32.c
/have-fun-debugging/linux-5.15/arch/x86/entry/syscalls
/have-fun-debugging/linux-5.15/arch/x86/entry/syscalls/syscall_32.tbl
/have-fun-debugging/linux-5.15/arch/x86/entry/syscalls/syscall_64.tbl
/have-fun-debugging/linux-5.15/arch/x86/entry/syscall_64.c
/have-fun-debugging/linux-5.15/arch/x86/entry/syscall_x32.c
/have-fun-debugging/linux-5.15/arch/x86/entry/syscall_32.c
/have-fun-debugging/linux-5.15/arch/arc/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/arc/include/asm/syscalls.h
/have-fun-debugging/linux-5.15/arch/openrisc/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/openrisc/include/asm/syscalls.h
/have-fun-debugging/linux-5.15/arch/mips/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/mips/kernel/syscalls
/have-fun-debugging/linux-5.15/arch/mips/kernel/syscalls/syscall_n64.tbl
/have-fun-debugging/linux-5.15/arch/mips/kernel/syscalls/syscall_n32.tbl
/have-fun-debugging/linux-5.15/arch/mips/kernel/syscalls/syscallnr.sh
/have-fun-debugging/linux-5.15/arch/mips/kernel/syscalls/syscall_o32.tbl
/have-fun-debugging/linux-5.15/arch/mips/kernel/syscall.c
/have-fun-debugging/linux-5.15/arch/hexagon/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/hexagon/kernel/syscalltab.c
/have-fun-debugging/linux-5.15/arch/riscv/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/riscv/kernel/syscall_table.c
/have-fun-debugging/linux-5.15/arch/powerpc/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/powerpc/include/asm/syscalls.h
/have-fun-debugging/linux-5.15/arch/powerpc/kernel/syscalls
/have-fun-debugging/linux-5.15/arch/powerpc/kernel/syscalls/syscall.tbl
/have-fun-debugging/linux-5.15/arch/powerpc/kernel/syscalls.c
/have-fun-debugging/linux-5.15/arch/powerpc/platforms/cell/spufs/syscalls.c
/have-fun-debugging/linux-5.15/arch/nios2/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/nios2/include/asm/syscalls.h
/have-fun-debugging/linux-5.15/arch/nios2/kernel/syscall_table.c
/have-fun-debugging/linux-5.15/arch/h8300/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/h8300/kernel/syscalls.c
/have-fun-debugging/linux-5.15/arch/um/include/asm/syscall-generic.h
/have-fun-debugging/linux-5.15/arch/um/kernel/skas/syscall.c
/have-fun-debugging/linux-5.15/arch/um/kernel/syscall.c
/have-fun-debugging/linux-5.15/arch/ia64/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/ia64/kernel/syscalls
/have-fun-debugging/linux-5.15/arch/ia64/kernel/syscalls/syscall.tbl
/have-fun-debugging/linux-5.15/arch/csky/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/csky/include/asm/syscalls.h
/have-fun-debugging/linux-5.15/arch/csky/kernel/syscall_table.c
/have-fun-debugging/linux-5.15/arch/csky/kernel/syscall.c
/have-fun-debugging/linux-5.15/arch/arm64/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/arm64/include/asm/syscall_wrapper.h
/have-fun-debugging/linux-5.15/arch/arm64/kernel/syscall.o
/have-fun-debugging/linux-5.15/arch/arm64/kernel/syscall.c
/have-fun-debugging/linux-5.15/arch/m68k/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/m68k/kernel/syscalls
/have-fun-debugging/linux-5.15/arch/m68k/kernel/syscalls/syscall.tbl
/have-fun-debugging/linux-5.15/arch/m68k/kernel/syscalltable.S
/have-fun-debugging/linux-5.15/arch/s390/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/s390/include/asm/syscall_wrapper.h
/have-fun-debugging/linux-5.15/arch/s390/kernel/syscalls
/have-fun-debugging/linux-5.15/arch/s390/kernel/syscalls/syscall.tbl
/have-fun-debugging/linux-5.15/arch/s390/kernel/syscalls/syscalltbl
/have-fun-debugging/linux-5.15/arch/s390/kernel/syscall.c
/have-fun-debugging/linux-5.15/arch/sh/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/sh/include/asm/syscall_32.h
/have-fun-debugging/linux-5.15/arch/sh/include/asm/syscalls.h
/have-fun-debugging/linux-5.15/arch/sh/include/asm/syscalls_32.h
/have-fun-debugging/linux-5.15/arch/sh/kernel/syscalls_32.S
/have-fun-debugging/linux-5.15/arch/sh/kernel/syscalls
/have-fun-debugging/linux-5.15/arch/sh/kernel/syscalls/syscall.tbl
/have-fun-debugging/linux-5.15/arch/microblaze/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/microblaze/kernel/syscall_table.S
/have-fun-debugging/linux-5.15/arch/microblaze/kernel/syscalls
/have-fun-debugging/linux-5.15/arch/microblaze/kernel/syscalls/syscall.tbl
/have-fun-debugging/linux-5.15/arch/sparc/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/sparc/include/asm/syscalls.h
/have-fun-debugging/linux-5.15/arch/sparc/kernel/syscalls
/have-fun-debugging/linux-5.15/arch/sparc/kernel/syscalls/syscall.tbl
/have-fun-debugging/linux-5.15/arch/sparc/kernel/syscalls.S
/have-fun-debugging/linux-5.15/arch/alpha/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/alpha/kernel/syscalls
/have-fun-debugging/linux-5.15/arch/alpha/kernel/syscalls/syscall.tbl
/have-fun-debugging/linux-5.15/arch/parisc/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/parisc/kernel/syscalls
/have-fun-debugging/linux-5.15/arch/parisc/kernel/syscalls/syscall.tbl
/have-fun-debugging/linux-5.15/arch/parisc/kernel/syscall.S
/have-fun-debugging/linux-5.15/arch/nds32/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/nds32/include/asm/syscalls.h
/have-fun-debugging/linux-5.15/arch/nds32/kernel/syscall_table.c
/have-fun-debugging/linux-5.15/arch/xtensa/include/asm/syscall.h
/have-fun-debugging/linux-5.15/arch/xtensa/kernel/syscalls
/have-fun-debugging/linux-5.15/arch/xtensa/kernel/syscalls/syscall.tbl
/have-fun-debugging/linux-5.15/arch/xtensa/kernel/syscall.c
/have-fun-debugging/linux-5.15/include/trace/syscall.h
/have-fun-debugging/linux-5.15/include/trace/events/syscalls.h
/have-fun-debugging/linux-5.15/include/linux/syscalls.h
/have-fun-debugging/linux-5.15/include/linux/syscall_user_dispatch.h
/have-fun-debugging/linux-5.15/include/asm-generic/syscall.h
/have-fun-debugging/linux-5.15/include/asm-generic/syscalls.h
/have-fun-debugging/linux-5.15/security/landlock/syscalls.c
/have-fun-debugging/linux-5.15/ipc/syscall.o
/have-fun-debugging/linux-5.15/ipc/syscall.c
/have-fun-debugging/linux-5.15/kernel/bpf/syscall.c
/have-fun-debugging/linux-5.15/kernel/entry/syscall_user_dispatch.c
/have-fun-debugging/linux-5.15/drivers/pci/syscall.o
/have-fun-debugging/linux-5.15/drivers/pci/syscall.c
/have-fun-debugging/linux-5.15/scripts/syscallnr.sh
/have-fun-debugging/linux-5.15/scripts/syscallhdr.sh
/have-fun-debugging/linux-5.15/scripts/syscalltbl.sh
/have-fun-debugging/linux-5.15/samples/bpf/syscall_nrs.c
/have-fun-debugging/linux-5.15/samples/bpf/syscall_tp_user.c
/have-fun-debugging/linux-5.15/samples/bpf/syscall_tp_kern.c
/have-fun-debugging/linux-5.15/tools/perf/util/syscalltbl.c
/have-fun-debugging/linux-5.15/tools/perf/util/syscalltbl.h
/have-fun-debugging/linux-5.15/tools/perf/arch/x86/entry/syscalls
/have-fun-debugging/linux-5.15/tools/perf/arch/x86/entry/syscalls/syscall_64.tbl
/have-fun-debugging/linux-5.15/tools/perf/arch/x86/entry/syscalls/syscalltbl.sh
/have-fun-debugging/linux-5.15/tools/perf/arch/mips/entry/syscalls
/have-fun-debugging/linux-5.15/tools/perf/arch/mips/entry/syscalls/syscall_n64.tbl
/have-fun-debugging/linux-5.15/tools/perf/arch/powerpc/entry/syscalls
/have-fun-debugging/linux-5.15/tools/perf/arch/powerpc/entry/syscalls/syscall.tbl
/have-fun-debugging/linux-5.15/tools/perf/arch/arm64/entry/syscalls
/have-fun-debugging/linux-5.15/tools/perf/arch/s390/entry/syscalls
/have-fun-debugging/linux-5.15/tools/perf/arch/s390/entry/syscalls/syscall.tbl
/have-fun-debugging/linux-5.15/tools/perf/bench/syscall.c
/have-fun-debugging/linux-5.15/tools/perf/scripts/python/bin/syscall-counts-record
/have-fun-debugging/linux-5.15/tools/perf/scripts/python/bin/syscall-counts-by-pid-report
/have-fun-debugging/linux-5.15/tools/perf/scripts/python/bin/syscall-counts-report
/have-fun-debugging/linux-5.15/tools/perf/scripts/python/bin/syscall-counts-by-pid-record
/have-fun-debugging/linux-5.15/tools/perf/scripts/python/syscall-counts-by-pid.py
/have-fun-debugging/linux-5.15/tools/perf/scripts/python/syscall-counts.py
/have-fun-debugging/linux-5.15/tools/testing/selftests/bpf/progs/syscall.c
/have-fun-debugging/linux-5.15/tools/testing/selftests/bpf/prog_tests/syscall.c
/have-fun-debugging/linux-5.15/tools/testing/selftests/x86/syscall_nt.c
/have-fun-debugging/linux-5.15/tools/testing/selftests/x86/syscall_numbering.c
/have-fun-debugging/linux-5.15/tools/testing/selftests/x86/syscall_arg_fault.c
/have-fun-debugging/linux-5.15/tools/testing/selftests/powerpc/syscalls
/have-fun-debugging/linux-5.15/tools/testing/selftests/arm64/bti/syscall.S
/have-fun-debugging/linux-5.15/tools/testing/selftests/syscall_user_dispatch
/have-fun-debugging/linux-5.15/tools/io_uring/syscall.c
```

里面找到了那么几个有用的 ARM32, RISC-V(32 bit), RISC-V(64 bit), x86(32 bit), x86_64

- /have-fun-debugging/linux-5.15/arch/riscv/kernel/syscall_table.c
- /have-fun-debugging/linux-5.15/arch/x86/entry/syscalls/syscall_64.tbl
- /have-fun-debugging/linux-5.15/arch/x86/entry/syscalls/syscall_32.tbl
- /have-fun-debugging/linux-5.15/arch/arm/tools/syscall.tbl

```
#cat arch/x86/entry/syscalls/syscall_64.tbl
可直接在terminal里查看tbl文件，下面三个都可以这样看到system call table
```

riscv的

```
#make ARCH=riscv CROSS_COMPILE=riscv64-unknown-linux-gnu- arch/riscv/kernel/syscall_table.i -j$(nproc)
这里要注意中间是.i不是.c，中间是目标文件
```

然后就能看到有一个数组存着system call table了

![image-20211125151836302](C:\Users\86181\Desktop\image-20211125151836302.png)