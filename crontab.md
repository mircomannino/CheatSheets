## Crontab cheat sheet

#### SHORT DESCRIPTION
Crontab is a linux command-line tool that allow to schedule in a very efficient way your task

---

#### OPEN CONFIGURATION FILE
```bash
user@machine crontab -e
```

---

#### CRONTAB FILE FORMAT
The format is the following 
> ```minute```  ```hour```  ```day-of-month``` ```month``` ```day-of-week``` command

The possible values are:

* ```minute```: [0-59]
* ```hour```: [0-23]
* ```day-of-month```: [1-31] 
* ```month```: [1-12]
* ```day-of-week```: [0-7] Sunday is both 0 and 7.

###### NOTE
If both ```day-of-month``` and ```day-of-week``` are present, the command will be executed when at least one of them is true.

Example
```bash
### Schedule command every day at 22 30
30 22 * * * /path/to/my/command

### Schedule command every twenty minutes betwen 8 to 17, on Monday to Friday
0,20,40 8-17 * * 1-5 /path/to/my/command
```

---

