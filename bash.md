## Bash scripting cheat sheet
Cheat sheet of bash scripting commands.

#### <span style="color:purple"> BASH INTERPRETER </span>
Always start your *.sh file with:
```bash
#!/bin/bash
```

---

#### <span style="color:purple"> IF-ELSE STATEMENT </span>
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

https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php

---
