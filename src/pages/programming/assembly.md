# Assembly

Assembly is a family of low-level programming languages that are very close to
the hardware. This might be needed for time-critical applications or if
applications are limited in memory, which is common in spacecrafts.

Here is an example of the assembly code of a C hello world program (using
`layout asm` in `gdb`).

```
0x64a <main>                    push   %rbp
0x64b <main+1>                  mov    %rsp,%rbp
0x64e <main+4>                  sub    $0x10,%rsp
0x652 <main+8>                  mov    %edi,-0x4(%rbp)
0x655 <main+11>                 mov    %rsi,-0x10(%rbp)
0x659 <main+15>                 lea    0x9c(%rip),%rdi
0x660 <main+22>                 callq  0x520 <puts@plt>
0x665 <main+27>                 mov    $0x0,%eax
0x66a <main+32>                 leaveq
0x66b <main+33>                 retq
```
