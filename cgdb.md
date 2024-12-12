# CGDB

## Debug

* **compile:**  `gcc -g -o pwd_checker test_pwd_checker.c pwd_checker.c`
* **start cgdb:**  `cgdb pwd_checker`
* **start debuging:** "start"
* **switch to code:** "ESC"
* **switch to CML:** "i"
* exit: "q"

## CGDB 安装（Windows）

1，安装WSL

2，pre-requirements

sudo apt-get install automake libncurses5-dev flex texinfo libreadline-dev

3，下载安装包

*   方法一：从git安装\


    ```
    # latest sources should be newer than version 0.7.1
    git clone https://github.com/cgdb/cgdb.git 
    cd cgdb
    mkdir build
    ./autogen.sh
    cd build
    ../configure
    make -j8
    sudo make install
    ```
*   方法二：单独下载gz安装包安装：\
    下载gz安装包，在WSL控制台用copy指令copy到ubuntu目录（Download），解压 \
    $ sudo tar -xzvf cgdb-0.8.0.tar.gz\
    并且进入解压之后的目录。\
    然后编译并且进行安装：

    <pre><code><strong>$ ./configure --prefix=/usr/local 
    </strong>$ sudo make 
    $ sudo make install
    </code></pre>

