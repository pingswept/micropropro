---
title: "Compilation example"
draft: false
---

## Example of compiling C code ##

Suppose you want to compile a short C program into machine code, the bits that your microcontroller can execute.

Let's start with a stupidly simple program, called `simple.c`.

```c
void main() {
    int x = 255;
    x = x + 0xAAAA;
}
```

On a Raspberry Pi, I could compile that like this: `gcc simple.c`.

(GCC is the Gnu C compiler. It's a ubiquitous free, open source C compiler, licensed under the GPL. The other major player in the open source compiler world is Clang/LLVM, which uses a BSD-style license. Anyway, `gcc` is installed by default on the Pi, so we'll stick with that.)

This takes the 53-byte C file we started with and turns it into a 7912-byte binary, called `a.out` by default.

We can look at some of the steps along the way.

`gcc -S simple.c` just compiles the C into assembly, but doesn't translate that into machine code.

```sh
pi@raspberrypi:~ $ ls -l
total 20
-rwxr-xr-x 1 pi pi 7912 Dec 11 15:30 a.out
-rw-r--r-- 1 pi pi   53 Dec 11 14:42 simple.c
-rw-r--r-- 1 pi pi  852 Dec 11 15:30 simple.o
-rw-r--r-- 1 pi pi  807 Dec 11 14:56 simple.s
```

Here are the contents of simple.s.

```sh
pi@raspberrypi:~ $ cat simple.s
        .arch armv6
        .eabi_attribute 28, 1
        .eabi_attribute 20, 1
        .eabi_attribute 21, 1
        .eabi_attribute 23, 3
        .eabi_attribute 24, 1
        .eabi_attribute 25, 1
        .eabi_attribute 26, 2
        .eabi_attribute 30, 6
        .eabi_attribute 34, 1
        .eabi_attribute 18, 4
        .file   "simple.c"
        .text
        .align  2
        .global main
        .arch armv6
        .syntax unified
        .arm
        .fpu vfp
        .type   main, %function
main:
        @ args = 0, pretend = 0, frame = 8
        @ frame_needed = 1, uses_anonymous_args = 0
        @ link register save eliminated.
        str     fp, [sp, #-4]!
        add     fp, sp, #0
        sub     sp, sp, #12
        mov     r3, #255
        str     r3, [fp, #-8]
        ldr     r3, [fp, #-8]
        add     r3, r3, #43520
        add     r3, r3, #170
        str     r3, [fp, #-8]
        nop
        add     sp, fp, #0
        @ sp needed
        ldr     fp, [sp], #4
        bx      lr
        .size   main, .-main
        .ident  "GCC: (Raspbian 8.3.0-6+rpi1) 8.3.0"
        .section        .note.GNU-stack,"",%progbits
```

The lines that start with `@` are just comments.

The crux of the program is in three lines

```
        mov     r3, #255
        ...
        add     r3, r3, #43520
        add     r3, r3, #170
```

Note that 43520 is the same as 0xAA00, and 170 is the same as 0x00AA.

All the sp and fp stuff deal with stack pointer and frame pointer, respectively. The last line `bx lr` just means "return from the function using the address in the link register." (`bx` stands for "branch and exchange.")

`gcc -c simple.c` compiles the C code to assembly, and then translates that into machine code.

```sh
pi@raspberrypi:~ $ xxd simple.o
00000000: 7f45 4c46 0101 0100 0000 0000 0000 0000  .ELF............
00000010: 0100 2800 0100 0000 0000 0000 0000 0000  ..(.............
00000020: c401 0000 0000 0005 3400 0000 0000 2800  ........4.....(.
00000030: 0a00 0900 04b0 2de5 00b0 8de2 0cd0 4de2  ......-.......M.
00000040: ff30 a0e3 0830 0be5 0830 1be5 aa3c 83e2  .0...0...0...<..
00000050: aa30 83e2 0830 0be5 0000 a0e1 00d0 8be2  .0...0..........
00000060: 04b0 9de4 1eff 2fe1 0047 4343 3a20 2852  ....../..GCC: (R
00000070: 6173 7062 6961 6e20 382e 332e 302d 362b  aspbian 8.3.0-6+
00000080: 7270 6931 2920 382e 332e 3000 412e 0000  rpi1) 8.3.0.A...
00000090: 0061 6561 6269 0001 2400 0000 0536 0006  .aeabi..$....6..
000000a0: 0608 0109 010a 0212 0414 0115 0117 0318  ................
000000b0: 0119 011a 021c 011e 0622 0100 0000 0000  ........."......
000000c0: 0000 0000 0000 0000 0000 0000 0100 0000  ................
000000d0: 0000 0000 0000 0000 0400 f1ff 0000 0000  ................
000000e0: 0000 0000 0000 0000 0300 0100 0000 0000  ................
000000f0: 0000 0000 0000 0000 0300 0200 0000 0000  ................
00000100: 0000 0000 0000 0000 0300 0300 0a00 0000  ................
00000110: 0000 0000 0000 0000 0000 0100 0000 0000  ................
00000120: 0000 0000 0000 0000 0300 0500 0000 0000  ................
00000130: 0000 0000 0000 0000 0300 0400 0000 0000  ................
00000140: 0000 0000 0000 0000 0300 0600 0d00 0000  ................
00000150: 0000 0000 3400 0000 1200 0100 0073 696d  ....4........sim
00000160: 706c 652e 6300 2461 006d 6169 6e00 002e  ple.c.$a.main...
00000170: 7379 6d74 6162 002e 7374 7274 6162 002e  symtab..strtab..
00000180: 7368 7374 7274 6162 002e 7465 7874 002e  shstrtab..text..
00000190: 6461 7461 002e 6273 7300 2e63 6f6d 6d65  data..bss..comme
000001a0: 6e74 002e 6e6f 7465 2e47 4e55 2d73 7461  nt..note.GNU-sta
000001b0: 636b 002e 4152 4d2e 6174 7472 6962 7574  ck..ARM.attribut
000001c0: 6573 0000 0000 0000 0000 0000 0000 0000  es..............
000001d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
000001e0: 0000 0000 0000 0000 0000 0000 1b00 0000  ................
000001f0: 0100 0000 0600 0000 0000 0000 3400 0000  ............4...
00000200: 3400 0000 0000 0000 0000 0000 0400 0000  4...............
00000210: 0000 0000 2100 0000 0100 0000 0300 0000  ....!...........
00000220: 0000 0000 6800 0000 0000 0000 0000 0000  ....h...........
00000230: 0000 0000 0100 0000 0000 0000 2700 0000  ............'...
00000240: 0800 0000 0300 0000 0000 0000 6800 0000  ............h...
00000250: 0000 0000 0000 0000 0000 0000 0100 0000  ................
00000260: 0000 0000 2c00 0000 0100 0000 3000 0000  ....,.......0...
00000270: 0000 0000 6800 0000 2400 0000 0000 0000  ....h...$.......
00000280: 0000 0000 0100 0000 0100 0000 3500 0000  ............5...
00000290: 0100 0000 0000 0000 0000 0000 8c00 0000  ................
000002a0: 0000 0000 0000 0000 0000 0000 0100 0000  ................
000002b0: 0000 0000 4500 0000 0300 0070 0000 0000  ....E......p....
000002c0: 0000 0000 8c00 0000 2f00 0000 0000 0000  ......../.......
000002d0: 0000 0000 0100 0000 0000 0000 0100 0000  ................
000002e0: 0200 0000 0000 0000 0000 0000 bc00 0000  ................
000002f0: a000 0000 0800 0000 0900 0000 0400 0000  ................
00000300: 1000 0000 0900 0000 0300 0000 0000 0000  ................
00000310: 0000 0000 5c01 0000 1200 0000 0000 0000  ....\...........
00000320: 0000 0000 0100 0000 0000 0000 1100 0000  ................
00000330: 0300 0000 0000 0000 0000 0000 6e01 0000  ............n...
00000340: 5500 0000 0000 0000 0000 0000 0100 0000  U...............
00000350: 0000 0000                                ....
```

We can disassemble this with ` objdump`.

```sh
pi@raspberrypi:~ $ objdump -d simple.o
simple.o:     file format elf32-littlearm
Disassembly of section .text:
00000000 <main>:
   0:   e52db004        push    {fp}            ; (str fp, [sp, #-4]!)
   4:   e28db000        add     fp, sp, #0
   8:   e24dd00c        sub     sp, sp, #12
   c:   e3a030ff        mov     r3, #255        ; 0xff
  10:   e50b3008        str     r3, [fp, #-8]
  14:   e51b3008        ldr     r3, [fp, #-8]
  18:   e2833caa        add     r3, r3, #43520  ; 0xaa00
  1c:   e28330aa        add     r3, r3, #170    ; 0xaa
  20:   e50b3008        str     r3, [fp, #-8]
  24:   e1a00000        nop                     ; (mov r0, r0)
  28:   e28bd000        add     sp, fp, #0
  2c:   e49db004        pop     {fp}            ; (ldr fp, [sp], #4)
  30:   e12fff1e        bx      lr
```

More info about shrinking binaries: https://journal.lunar.sh/2020/10/24/tiny-linux-c-binaries.html
