# **REVERSE ENGINEERING**
## **<ins>ARMssembly 1</ins>**
### CHALLENGE DESCRIPTION:
For what argument does this program print `win` with variables 68, 2 and 3? File: chall_1.S
Flag format: picoCTF{XXXXXXXX} -> (hex, lowercase, no 0x, and 32 bits. ex. 5614267 would be picoCTF{0055aabb})

```
	str	w0, [sp, 12] 
	mov	w0, 68
	str	w0, [sp, 16]. [sp,16] = 68
	mov	w0, 2
	str	w0, [sp, 20]. [sp,20] = 2
	mov	w0, 3
	str	w0, [sp, 24]. [sp,24] = 3
	ldr	w0, [sp, 20]. w0 = 2
	ldr	w1, [sp, 16]. w1 = 68
	lsl	w0, w1, w0. w0 = 68 << 2 = 272 → stored at [sp,28].
	str	w0, [sp, 28] 
	ldr	w1, [sp, 28]. w1 = 272
	ldr	w0, [sp, 24]. w0 = 3
	sdiv	w0, w1, w0. w0 = 272 / 3 = 90, stored at [sp,28].
	str	w0, [sp, 28]
	ldr	w1, [sp, 28]. w1 = 90
	ldr	w0, [sp, 12]. w0 = original_argument
	sub	w0, w1, w0. w0 = 90 - original_argument returned.
	str	w0, [sp, 28]
	ldr	w0, [sp, 28]
	add	sp, sp, 32
```
lsl	w0, w1, w0. 
means Take the number in w1 (68)
Shift it left by the number in w0 (2 places)
Store the result back in w0.
68 = 01000100 (in binary)
01000100 << 2 = 000100010000
000100010000 = 272 when converted back to decimal.

When 90 is converted to 32 bit hex 0x0000005a → 0000005a.
Hence the flag is picoCTF{0000005a}


### SOLVE: 
***FLAG:***: picoCTF{0000005a}

## Concepts learnt:
I learnt ldr → load a value from memory into a register 
lsl → logical shift left (multiply by powers of 2)
sdiv → signed divide
sub → subtraction
ret → return from the function
