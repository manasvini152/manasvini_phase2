# **BINARY EXP**
## **<ins>BUFFER OVERFLOW 0</ins>**
### CHALLENGE DESCRIPTION:
Let's start off simple, can you overflow the correct buffer? The program is available here. You can view source here.
Additional details will be available after launching your challenge instance.
How can you trigger the flag to print?
If you try to do the math by hand, maybe try and add a few more characters. Sometimes there are things you aren't expecting.
Run man gets and read the BUGS section. How many characters can the program really read?


I ran the command  nc saturn.picoctf.net 57756 in the webshell which ran the program and accepted an input.
I entered a sample input 10 which terminated the program.
Then I went through the source code of the program and the character variable buf2 has a 16 character limit.
And as the hints suggested to trigger the program to print the flag by adding a few more characters.
I entered an input of more than 16 characters which gave the flag.

```
manasvini152-picoctf@webshell:~$ nc saturn.picoctf.net 57756
Input: 11111111111111111111111
picoCTF{ov3rfl0ws_ar3nt_that_bad_9f2364bc}
```


### SOLVE: 
***FLAG:***:  picoCTF{ov3rfl0ws_ar3nt_that_bad_9f2364bc}

## Concepts learnt:
I learnt how to read C a program and trigger the program into giving the flag.

## Resources:
None.
