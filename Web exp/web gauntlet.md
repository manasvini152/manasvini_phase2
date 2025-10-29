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

I used the command admin' /* which is used to bypass a web application's login form and gain unauthorized access to an account.
This finds the database record for the admin user.
/*: This is the multi-line comment syntax that causes the rest of the query to be ignored. 


<img width="902" height="422" alt="image" src="https://github.com/user-attachments/assets/78a9ac3c-dcba-4243-be1b-90ec47aacc91" />
<img width="206" height="39" alt="image" src="https://github.com/user-attachments/assets/ffd9447a-e537-4cd1-8c24-acf69eaf04a5" />


Hence we enter round 3. 

Now since most of the commands like =, --, >, < are blocked we use the termination command ';'.
Hence by using the command admin'; we enter the next round.

<img width="912" height="433" alt="image" src="https://github.com/user-attachments/assets/9543ee96-925e-42ca-ae0e-d171f260b3fd" />
<img width="240" height="27" alt="image" src="https://github.com/user-attachments/assets/1e9b2dc3-a8f3-494d-88e5-dd341244ab99" />

Hence we enter round 4.

Now the admin command is also blocked hence we need to use the conactenation operator to use the keyword admin.
Hence by using the command ad'||'min'; we enter the next round.
The operator || combines ad and min into admin.
<img width="904" height="430" alt="image" src="https://github.com/user-attachments/assets/0c4389a1-2fba-4ee0-ab21-319bdae6e78a" />
<img width="303" height="40" alt="image" src="https://github.com/user-attachments/assets/0d0c6caf-97eb-42bf-910f-a715f471803a" />


Hence we enter round 5.

The concat operator is not blocked hence we can use the same command as the previous round.
<img width="908" height="429" alt="image" src="https://github.com/user-attachments/assets/29a6a67d-0ca6-400a-b7e0-87f08142e5c5" />
```
<?php
session_start();

if (!isset($_SESSION["round"])) {
    $_SESSION["round"] = 1;
}
$round = $_SESSION["round"];
$filter = array("");
$view = ($_SERVER["PHP_SELF"] == "/filter.php");

if ($round === 1) {
    $filter = array("or");
    if ($view) {
        echo "Round1: ".implode(" ", $filter)."<br/>";
    }
} else if ($round === 2) {
    $filter = array("or", "and", "like", "=", "--");
    if ($view) {
        echo "Round2: ".implode(" ", $filter)."<br/>";
    }
} else if ($round === 3) {
    $filter = array(" ", "or", "and", "=", "like", ">", "<", "--");
    // $filter = array("or", "and", "=", "like", "union", "select", "insert", "delete", "if", "else", "true", "false", "admin");
    if ($view) {
        echo "Round3: ".implode(" ", $filter)."<br/>";
    }
} else if ($round === 4) {
    $filter = array(" ", "or", "and", "=", "like", ">", "<", "--", "admin");
    // $filter = array(" ", "/**/", "--", "or", "and", "=", "like", "union", "select", "insert", "delete", "if", "else", "true", "false", "admin");
    if ($view) {
        echo "Round4: ".implode(" ", $filter)."<br/>";
    }
} else if ($round === 5) {
    $filter = array(" ", "or", "and", "=", "like", ">", "<", "--", "union", "admin");
    // $filter = array("0", "unhex", "char", "/*", "*/", "--", "or", "and", "=", "like", "union", "select", "insert", "delete", "if", "else", "true", "false", "admin");
    if ($view) {
        echo "Round5: ".implode(" ", $filter)."<br/>";
    }
} else if ($round >= 6) {
    if ($view) {
        highlight_file("filter.php");
    }
} else {
    $_SESSION["round"] = 1;
}

// picoCTF{y0u_m4d3_1t_79a0ddc6}
?>
```

### SOLVE: 
***FLAG:***: picoCTF{y0u_m4d3_1t_79a0ddc6}

## Concepts learnt:
I learnt various sql command and how to bypass a login page using admin access.

## Resources:
None.
