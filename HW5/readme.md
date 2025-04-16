## 陳家盛 power.c

產生組合語言.s檔
```
gcc -S 0326.c
```
執行power.c
```
 gcc power.c
 ./a.exe
```
產生目的檔.o檔
```
gcc -c power.c
```
將該目的檔反組譯
```
objdump -d power.o
```
```sh
power.o:     file format pe-i386


Disassembly of section .text:

00000000 <_power>:
   0:   55                      push   %ebp
   1:   89 e5                   mov    %esp,%ebp
   3:   83 ec 10                sub    $0x10,%esp
   6:   c7 45 fc 01 00 00 00    movl   $0x1,-0x4(%ebp)
   d:   c7 45 f8 00 00 00 00    movl   $0x0,-0x8(%ebp)
  14:   eb 0e                   jmp    24 <_power+0x24>
  16:   8b 45 fc                mov    -0x4(%ebp),%eax
  19:   0f af 45 08             imul   0x8(%ebp),%eax
  1d:   89 45 fc                mov    %eax,-0x4(%ebp)
  20:   83 45 f8 01             addl   $0x1,-0x8(%ebp)
  24:   8b 45 f8                mov    -0x8(%ebp),%eax
  27:   3b 45 0c                cmp    0xc(%ebp),%eax
  2a:   7c ea                   jl     16 <_power+0x16>
  2c:   8b 45 fc                mov    -0x4(%ebp),%eax
  2f:   c9                      leave  
  30:   c3                      ret
  31:   90                      nop
  32:   90                      nop
  33:   90                      nop
```
印出該目的檔的表頭
```
objdump -h power.o
```
```sh
power.o:     file format pe-i386

Sections:
Idx Name          Size      VMA       LMA       File off  Algn
  0 .text         00000034  00000000  00000000  000000dc  2**2
                  CONTENTS, ALLOC, LOAD, READONLY, CODE
  1 .data         00000000  00000000  00000000  00000000  2**2
                  ALLOC, LOAD, DATA
  2 .bss          00000000  00000000  00000000  00000000  2**2
                  ALLOC
  3 .rdata$zzz    00000024  00000000  00000000  00000110  2**2
                  CONTENTS, ALLOC, LOAD, READONLY, DATA
  4 .eh_frame     00000038  00000000  00000000  00000134  2**2
                  CONTENTS, ALLOC, LOAD, RELOC, READONLY, DATA
```
