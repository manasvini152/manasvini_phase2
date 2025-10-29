# **WEB EXP**
## **<ins>COOKIES</ins>**
### CHALLENGE DESCRIPTION:
Who doesn't love cookies? Try to figure out the best one. http://mercury.picoctf.net:21485/

After opening the link I entered snickerdoodle and inspected the page.
Under applications and cookies the value was 0.
<img width="1228" height="497" alt="image" src="https://github.com/user-attachments/assets/28fccb70-6f83-4abe-9072-e7daca111740" />

Then I tried changing the value to another number ( 1 ) and after refreshing the page it was chocolate chip cookies.

<img width="1360" height="385" alt="image" src="https://github.com/user-attachments/assets/b1eb30b1-2f29-4057-97fe-fcef34355314" />

Thus every different number has different cookies.
I then tried the number 50, but the page was not valid.
The values above 28 gave me an error.
Thus I tried the values below 28.
And at the value 18 I obtained the flag.
<img width="1287" height="158" alt="image" src="https://github.com/user-attachments/assets/b5be005d-b270-4bf9-8a32-f16b6ce58b7f" />


### SOLVE: 
***FLAG:***:   picoCTF{3v3ry1_l0v3s_c00k135_94190c8a}

## Concepts learnt:
I learnt about inspecting a web page and cookie values.
