# Buffer Overflow

Buffer overflow is a vulnerability where the buffer of one entity overflows into
another. This vulnerability is most prevalent in languages where memory
allocation is explicitly handled by the user, such as C and C++. Buffer overflow
can be used for binary exploitation.

One prominent example is when the buffer of one variable overflows into another,
which is demonstrated in the code below. This is due to `authenticated` being
declared after `password`.

```c
#include<string.h>
#include<stdio.h>

int main() {
  char password[4];
  int authenticated = 0;
  printf("\nEnter password:\n");
  scanf("%s", password);

  if (!strcmp(password, "abcd")) {
    authenticated = 1;
  }

  if (authenticated) {
    printf("\nAccess granted!");
  } else {
    printf("\nAccess denied!");
  }
}
```

As modern C compilers have some built in protections against overflow, this
program would have to be compiled as `gcc -fno-stack-protector -o vuln vuln.c`.
When running the program, access is granted for the password `abcd` but also for
any string that is longer than four characters.

Our next example is more surprising. Consider the following code snippet. Using
binary exploitation we can get `uncalled_function` to be executed.

```c
#include<stdio.h>
#include<string.h>

void uncalled_function() {
  printf("This function should never be called\n");
}

void called_function(char *args) {
  char buf[16];
  strcpy(buf, args);
  printf("Arg: %s\n", buf);
}

int main(int argc, char **argv) {
  if(argc >= 2) {
    called_function(argv[1]);
  }
  return 0;
}
```

The function can be run as

```sh
> gcc -o vuln.bin vuln.c
> ./vuln.bin $(python -c 'print("A"*16)')
```

We want to change the value of the `call` in the `main` function. We look up the
relative position of `call` in the disassembly code using the GNU debugger. On
my computer it is `35`.

```sh
> gdb -q ./vuln.bin
Reading symbols from ./vuln.bin...
(No debugging symbols found in ./vuln.bin)
(gdb) disas main
Dump of assembler code for function main:
   0x00000000000011df <+0>:	push   %rbp
   0x00000000000011e0 <+1>:	mov    %rsp,%rbp
   0x00000000000011e3 <+4>:	sub    $0x10,%rsp
   0x00000000000011e7 <+8>:	mov    %edi,-0x4(%rbp)
   0x00000000000011ea <+11>:	mov    %rsi,-0x10(%rbp)
   0x00000000000011ee <+15>:	cmpl   $0x1,-0x4(%rbp)
   0x00000000000011f2 <+19>:	jle    0x1207 <main+40>
   0x00000000000011f4 <+21>:	mov    -0x10(%rbp),%rax
   0x00000000000011f8 <+25>:	add    $0x8,%rax
   0x00000000000011fc <+29>:	mov    (%rax),%rax
   0x00000000000011ff <+32>:	mov    %rax,%rdi
   0x0000000000001202 <+35>:	call   0x117f <called_function>
   0x0000000000001207 <+40>:	mov    $0x0,%eax
   0x000000000000120c <+45>:	leave
   0x000000000000120d <+46>:	ret
End of assembler dump.
Dump of assembler code for function called_function:
   0x000000000000117f <+0>:	push   %rbp
   0x0000000000001180 <+1>:	mov    %rsp,%rbp
   0x0000000000001183 <+4>:	sub    $0x30,%rsp
   0x0000000000001187 <+8>:	mov    %rdi,-0x28(%rbp)
   0x000000000000118b <+12>:	mov    %fs:0x28,%rax
   0x0000000000001194 <+21>:	mov    %rax,-0x8(%rbp)
   0x0000000000001198 <+25>:	xor    %eax,%eax
   0x000000000000119a <+27>:	mov    -0x28(%rbp),%rdx
   0x000000000000119e <+31>:	lea    -0x20(%rbp),%rax
   0x00000000000011a2 <+35>:	mov    %rdx,%rsi
   0x00000000000011a5 <+38>:	mov    %rax,%rdi
   0x00000000000011a8 <+41>:	call   0x1030 <strcpy@plt>
   0x00000000000011ad <+46>:	lea    -0x20(%rbp),%rax
   0x00000000000011b1 <+50>:	mov    %rax,%rsi
   0x00000000000011b4 <+53>:	lea    0xe72(%rip),%rax        # 0x202d
   0x00000000000011bb <+60>:	mov    %rax,%rdi
   0x00000000000011be <+63>:	mov    $0x0,%eax
   0x00000000000011c3 <+68>:	call   0x1060 <printf@plt>
   0x00000000000011c8 <+73>:	nop
   0x00000000000011c9 <+74>:	mov    -0x8(%rbp),%rax
   0x00000000000011cd <+78>:	sub    %fs:0x28,%rax
   0x00000000000011d6 <+87>:	je     0x11dd <called_function+94>
   0x00000000000011d8 <+89>:	call   0x1050 <__stack_chk_fail@plt>
   0x00000000000011dd <+94>:	leave
   0x00000000000011de <+95>:	ret
```

Next up we need to find function address of `uncalled_function`. We accomplish
this using `objdump` and `grep`.

```sh
> objdump -d vuln.bin | rg uncalled_function
0000000000001169 <uncalled_function>:
```

Then we can construct our final command. We want to write to `36+4` positions (4
since my computer has 16 bit memory addresses which correspond to 4 ACII
characters). Then the command is:

```sh
> ./vuln.bin $(python -c 'print("A"*39 + "\x96\x11\x00\x00\x00\x00\x00\x00")')
This function should never be called
```

NB: I have not gotten this to work for myself yet but this should be one way of
doing it.
