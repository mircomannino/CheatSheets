## Bash scripting cheat sheet

### BASH INTERPRETER
Always start your *.sh file with:
```bash
#!/bin/bash
```

---

### IF-ELSE STATEMENT
The syntax for an if-else statement is the following:
```bash
if [ <condition> ]; then
    <command>
else
    <command>
fi
```
The ```<condition>``` could be one of the following:
| Operator | Description |
|:--------:|:-----------:|
| ! \<epression\> | The \<expression\> is false|
| -n \<string\> | The length of \<string\> is greater than zero|
| -z \<string\> | The lenght of the \<string\> is zero (i.e., it is empty)|
| \<string_1\> = \<string_2\> | \<string_1\> and \<string_2\> are the same|
| \<string_1\> != \<string_2\> | \<string_1\> and \<string_2\> are the different|

[1] https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php

---

### REPLACE A STRING
The syntax to replace a string is the following:
```bash
NEW_STRING = ${STRING//[<chars-to-replace>]/<new-char>}
```
An example:
```bash
MY_STRING="today_is_monday"
NEW_STRING=${MY_STRING//[_]/-}
echo NEW_STRING
# OUTPUT: today-is-monday
```

