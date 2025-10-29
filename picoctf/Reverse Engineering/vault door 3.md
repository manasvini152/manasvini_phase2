# **REVERSE ENGINEERING**
## **<ins>VAULT DOOR 3</ins>**
### CHALLENGE DESCRIPTION:
This vault uses for-loops and byte arrays. The source code for this vault is here: VaultDoor3.java


The given string was jU5t_a_sna_3lpm18gb41_u_4_mfr340.
By using the commands
```
for (i=0; i<8; i++) {
            buffer[i] = password.charAt(i);
        }
        for (; i<16; i++) {
            buffer[i] = password.charAt(23-i);
        }
        for (; i<32; i+=2) {
            buffer[i] = password.charAt(46-i);
        }
        for (i=31; i>=17; i-=2) {
            buffer[i] = password.charAt(i);
```

We shift the characters accordingly.
i value for the first for loop ranges from 0 to 7.
i value for the second for loop starts with 8 and goes till 15.
i value for the third for loop starts with 16 and goes till 31
i value for the fourth for loop starts with 32 and goes till 17.
Hence we shift the characters accordingly. and obtain the new string jU5t_a_s1mpl3_an4gr4m_4_u_1fb380.


### SOLVE: 
***FLAG:***:  picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_1fb380}

## Concepts learnt:
I learnt how to read the java codes and shift characters accordingly.

## Resources:
None.
