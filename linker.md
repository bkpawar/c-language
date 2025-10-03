# Assembly to Binary, QEMU and GDB
## Topic Overview

### Focus: Practical demonstration of assembly-to-binary workflow using QEMU emulator and GDB debugger

#### 1. Assembly to Binary Conversion Process 

 Assembly source file creation (.s or .asm)

 Assembler tool usage (likely GNU as or similar)

 Object file generation (.o files)

 Linker usage for final binary creation

 File format discussions (ELF, binary sections)

#### 2. QEMU Setup and Usage
 QEMU installation/setup

 Command line parameters for RISC-V emulation

 Loading binary files into QEMU

 QEMU monitor commands

 Memory mapping concepts

 Execution control in QEMU

4. Practical Commands to Record
bash
# Assembly compilation (example patterns to watch for)
``` riscv64-unknown-elf-gcc -O0 -ggdb -nostdlib -march=rv32i -mabi=ilp32 -Wl,-Tprogram.ld program.s
``` qemu-system-riscv32 -S -M virt -nographic -bios none -kernel program.elf -gdb tcp::1234

``` gdb-multiarch program.elf -ex "target remote localhost:1234" -ex "break _start" -ex "continue" -q
#### Generate the raw binary file without any debug info
``` riscv64-unknown-elf-objcopy -O binary program.elf program.bin

#### show the binary content from file
```` xxd -e -c 4 -g 4 program.bin

#### instruction decoder
```` https://luplab.gitlab.io/rvcodecjs/#q=addi&abi=false&isa=AUTO

#### paste the binary output of file, thats binary instruction

0000006f
its nothing but jmp instruction.