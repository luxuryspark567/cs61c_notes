# GDB

## Compile

*   Compile 1 file to 1 exe file, using the `-g` flag in case we need to debug this program in the future.

    ```bash
    gcc -g -o ex5_segfault ex5_segfault.c
    ```
*   Compile 2 files to 1 exe file.\


    ```bash
    gcc -g -o pwd_checker test_pwd_checker.c pwd_checker.c
    ```

## Run GDB

```
gdb pwd_checker
```

## GDB Commands

<table data-full-width="false"><thead><tr><th width="184">Command</th><th width="128">Abbreviation</th><th width="413">Description</th></tr></thead><tbody><tr><td>start</td><td>start</td><td>begin running the program and stop at line 1 in main</td></tr><tr><td>step</td><td>s</td><td>execute the current line of code (this command will step into functions)</td></tr><tr><td>next</td><td>n</td><td>execute the current line of code (this command will not step into functions)</td></tr><tr><td>finish</td><td>fin</td><td>executes the remainder of the current function and returns to the calling function</td></tr><tr><td>print [arg] </td><td>p</td><td>prints the value of the argument<br>(ex: for int n=3, print n will print out 3)</td></tr><tr><td>quit</td><td>q</td><td>exits gdb</td></tr><tr><td>break [line num or function name]</td><td>b</td><td>set a breakpoint at the specified location, use <mark style="color:red;">filename.c:linenum</mark> to set a breakpoint in a specific file<br>e.g. b pwd_checker.c:30</td></tr><tr><td>conditional break</td><td>(ex: b 3 if n==4)</td><td><p>set a breakpoint at the specified location only if a given condition is met<br>e.g. b pwd_checker.c:30 if letter == 'A'</p><p>e.g. b 3 if letter == 'A' (3 is break number, each breakpoint is assigned to a break number after created)</p></td></tr><tr><td>run</td><td>r</td><td>execute the program until termination or reaching a breakpoint</td></tr><tr><td>continue</td><td>c</td><td>continues the execution of a program that was paused</td></tr><tr><td>backtrace</td><td>bt</td><td>print one line per frame for frames in the stack</td></tr></tbody></table>

{% hint style="info" %}
1, After running into a break point, do not use "r" to continue runing: "r" will continue runing and restart the program, should use "c" to continue.
{% endhint %}

### Other Useful GDB Commands (Recommended) <a href="#other-useful-gdb-commands-recommended" id="other-useful-gdb-commands-recommended"></a>

#### Command: `info locals` <a href="#command-info-locals" id="command-info-locals"></a>

Prints the value of all of the local variables in the current stack frame

#### Command: `command` <a href="#command-command" id="command-command"></a>

Executes a list of commands every time a break point is reached. For example:

Set a breakpoint:

```txt
b 73
```

Type `commands` followed by the breakpoint number:

```txt
commands 1
```

Type the list of commands that you want to execute separated by a new line. After your list of commands, type `end` and hit Enter.

```txt
p var1
p var2
end
```
