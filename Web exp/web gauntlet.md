# **WEB EXP**
## **<ins>WEB GAUNTLET</ins>**
### CHALLENGE DESCRIPTION:
Can you beat the filters?
Log in as admin http://shape-facility.picoctf.net:54355/ http://shape-facility.picoctf.net:54355/filter.php

By running the command admin' -- we bypass the first page.
admin' -- is a classic sql command to bypass the login page as an admin.
The 'admin' part of the input closes the single quote for the username field and sets the username to admin.
The double-hyphen (--) is the SQL syntax for a comment. This tells the database to ignore the rest of the query on that line. Which is the password part of the command.

<img width="932" height="445" alt="image" src="https://github.com/user-attachments/assets/edb7387c-a15a-4a69-849c-0e76fe39e743" />
<img width="170" height="24" alt="image" src="https://github.com/user-attachments/assets/bb88db51-0665-4acc-bb51-44b50ab0fe3a" />

Hence we enter round 2.

