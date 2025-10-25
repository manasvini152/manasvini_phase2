# **REVERSE ENGINEERING**
## **<ins>GDB BABY STEP 1</ins>**
### CHALLENGE DESCRIPTION:
Can you figure out what is in the eax register at the end of the main function? Put your answer in the picoCTF flag format:
picoCTF{n} where n is the contents of the eax register in the decimal number base. If the answer was 0x11 your flag would be picoCTF{17}.
Disassemble this.

First I used the ls command to list out the files, through the picoctf webshell.
```
manasvini152-picoctf@webshell:~$ ls
README.txt
```

Then using the wget command followed by the link provided in the description I downloaded the file. 
And by using the ls command again the file was listed out.
```
manasvini152-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/512/debugger0_a
--2025-10-25 11:37:08--  https://artifacts.picoctf.net/c/512/debugger0_a
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.170.131.18, 3.170.131.77, 3.170.131.72, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.170.131.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16472 (16K) [application/octet-stream]
Saving to: 'debugger0_a'

debugger0_a         100%[==================>]  16.09K  --.-KB/s    in 0.006s  

2025-10-25 11:37:09 (2.61 MB/s) - 'debugger0_a' saved [16472/16472]

manasvini152-picoctf@webshell:~$ ls
README.txt  debugger0_a
```

Then I gave the executable permission to the file.
```
manasvini152-picoctf@webshell:~$ chmod +x debugger0_a
```
Then I initiated the GNU debugger which loads the file. 
```
manasvini152-picoctf@webshell:~$ gdb ./debugger0_a
GNU gdb (Ubuntu 12.1-0ubuntu1~22.04.2) 12.1
Copyright (C) 2022 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<https://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from ./debugger0_a...
(No debugging symbols found in ./debugger0_a)
(gdb)
```

Using the command disassemble /r main where, disassemble converts the mahcine level code to assembly level language.
/r instructs the GDB to display the raw hexadecimal values.
main is the standard entry point for C programs.
```
(gdb) disassemble /r main
Dump of assembler code for function main:
   0x0000000000001129 <+0>:     f3 0f 1e fa     endbr64 
   0x000000000000112d <+4>:     55      push   %rbp
   0x000000000000112e <+5>:     48 89 e5        mov    %rsp,%rbp
   0x0000000000001131 <+8>:     89 7d fc        mov    %edi,-0x4(%rbp)
   0x0000000000001134 <+11>:    48 89 75 f0     mov    %rsi,-0x10(%rbp)
   0x0000000000001138 <+15>:    b8 42 63 08 00  mov    $0x86342,%eax
   0x000000000000113d <+20>:    5d      pop    %rbp
   0x000000000000113e <+21>:    c3      ret    
End of assembler dump.
(gdb)
```

Using the q command we quit.
Then I used the python command to convert the hexadecimal number 0x86342 to decimal.
```
(gdb) q
manasvini152-picoctf@webshell:~$ python3 -c "print(0x86342)"
549698
```

As mentioned in the description the flag is in the format of picoCTF{ }
By entering the decimal value we get picoCTF{549698}


### SOLVE: 
***FLAG:***:  picoCTF{549698}

## Concepts learnt:
I learnt about GDB and various commands related to GDB.

## Resources:
None.









