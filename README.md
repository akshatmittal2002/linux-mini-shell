# Linux-Mini-Shell
This is a `C` code for Linux Shell (a mini version).<br>
The code is designed to work properly in `LINUX` terminal.<br>
***
<br>

To compile the code and run, use these commands on a linux terminal:<br>
```bash
1) gcc main.c

2) ./a.out
```
Mini shell will start in current working directory.

***
<br>

## List Of Operations:
<details>
<summary>1. setenv</summary>
<p><ul><li>Sets value of given environment variable to given value.</li></ul></p>
</details>

<details>
<summary>2. cd</summary>
<p><ul><li>All operations of cd command are replicated:
<ul>
<li>cd ..</li>
<li>cd</li>
<li>cd sub_directory</li>
<li>cd real_path</li>
</ul></li></ul>
</p>
</details>

<details>
<summary>3. history</summary>
<p><ul><li>Prints complete list of all commands used in mini-shell by user</li></ul></p>
</details>

<details>
<summary>4. quit / exit / x</summary>
<p><ul><li>Command to exit from the mini-shell</li></ul></p>
</details>

<details>
<summary>5. Piping ( | )</summary>
<p><ul><li>Single level piping can be done in my shell.</li>
<li>For example:
<ul>
<li>ls -lh | echo</li>
<li>cat file1.txt | wc</li>
</ul></li></ul>
</p>
</details>

<details>
<summary>6. Redirections</summary>
<p><ul><li>All sorts of redirections into/from files are handled:
<ul>
<li> &ltinput.txt </li>
<li> &gtoutput.txt </li>
<li> &gt&gtappend.txt </li>
<li> &ltinput.txt &gtoutput.txt </li>
<li> &ltinput.txt &gt&gtappend.txt </li>
</ul></li></ul>
</p>
</details>

<details>
<summary>7. Reasonable List of External LINUX commands</summary>
<p><ul><li>man, which, chsh, whereis, passwd, date, cal, clear, sleep, history, apropos, exit, logout, shutdown, ls, cat, more, less, touch, cp, mv, rm, script, find, mkdir, cd, pwd, rmdir, chmod, grep, etc.</li></ul></p>
</details>

***
<br>

### NOTE:
1. I have managed all whitespaces in input.<br>You can type your command in any format (with or without extra spaces).<br>It will be valid as long as it is valid in `LINUX Shell`.<br>Example: For `cat < file1.txt`, you can use:
    - cat < file1.txt
    - cat <file1.txt
    - cat< file1.txt
    - cat<file1.txt<br>
2. Run the command only in `LINUX Terminal` since some pre- installed libraries of `LINUX` are used in code.<br>
3. To view all logics and process followed, see the .c file.<br>Code is properly documented.

***
<br>

### A Brief Description:
1. An infinite while loop is created, printing current directory and waiting for single line user input.
2. If user calls for cd, then directory is changed to given path if the path exists.
3. If user calls setenv with proper format, then a new environment varibale is created with specified value. If environment variable already exists, then it's value is changed.
4. If user calls printenv, then:
	- If no envirionment varibale is given, all envirionment variables is printed with their values.
	- Else the values of specified variables are printed.
5. If user calls history, then the history file is printed.
6. If user type exit/quit/x, history file is deleted, all memory is freed, loop is broken and program terminates.
7. If there is piping in input, after all validity checks, two child processes are created and then both internal and external commands are executed.
8. If there is redirection, after all validity checks, a child process is created and both internal and external commands are executed with proper redirections to the files.
9. In all other cases, user input is executed using a child process and if anything invalid, error is displayed.
10. In all these cases, the input is saved in the history file in sequeunce.
11. Then all memory is freed and loop continues from step 1.

***