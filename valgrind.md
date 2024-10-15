# Valgrind

Valgrind is a program which <mark style="color:red;">emulates your CPU and tracks your memory accesses</mark>. This slows down the process you're running (which is why we don't, for example, always run all executables inside Valgrind) but also can expose bugs that may only display visible incorrect behavior under a unique set of circumstances.

## Install

`sudo apt-get install valgrind`

## Debug

* In general, to use valgrind you want to compile with the `-g` flag for debugging information (ie. `gcc -g -o example example.c`).&#x20;
* Then, run `valgrind` on the compiled executable (ie. `valgrind ./example`).&#x20;









