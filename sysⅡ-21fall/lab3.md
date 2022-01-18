```
/have-fun-debugging/sys2lab-21fall/src/lab3/linux/linux-5.15

$ qemu-system-riscv64 -nographic -machine virt -kernel /have-fun-debugging/sys2lab-21fall/src/lab3/linux/linux-5.15/arch/riscv/boot/Image \
    -device virtio-blk-device,drive=hd0 -append "root=/dev/vda ro console=ttyS0" \
    -bios default -drive file=rootfs.img,format=raw,id=hd0
    
    
qemu-system-riscv64 -nographic -machine virt -kernel /have-fun-debugging/sys2lab-21fall/src/lab3/linux/linux-5.15/arch/riscv/boot/Image \
    -device virtio-blk-device,drive=hd0 -append "root=/dev/vda ro console=ttyS0" \
    -bios default -drive file=rootfs.img,format=raw,id=hd0 -S -s
    
riscv64-unknown-linux-gnu-gdb /have-fun-debugging/sys2lab-21fall/src/lab3/linux/linux-5.15/to/linux/vmlinux
(gdb) target remote :1234   # 连接 qemu
(gdb) b start_kernel        # 设置断点
(gdb) continue              # 继续执行
(gdb) quit  
```

