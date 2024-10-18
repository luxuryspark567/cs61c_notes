# 环境准备

1，Git环境1，Git资料为SP22和FA24，视频主要为SP22，现在FA24的也可以下载了。实验和作业都参考FA24来。因为现在UCLA已经限制了访问，只能拿到最新的FA24的课程计划。这部分已经保存为PDF。

2，GCC安装​[https://cloud.tencent.com/developer/article/2339131](https://cloud.tencent.com/developer/article/2339131)​

3，CLI原始课程需要链接UCLA官方进行作业提交和审核，我们没有权限，只做Git提交，路径为：​[https://github.com/luxuryspark567/fa24-lab-starter](https://github.com/luxuryspark567/fa24-lab-starter)​

4，VIM编辑

| Command                | Explanation                                                                                                                             |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| vim xxx                | Open file xxx                                                                                                                           |
| i                      | Edit file                                                                                                                               |
| set number/set nu      | show line number                                                                                                                        |
| Esc `:q`               | Closes (quits) Vim without saving                                                                                                       |
| Esc `:wq`              | Closes Vim after saving                                                                                                                 |
| Esc `:w`               | Saves your file                                                                                                                         |
| Esc `:q!`              | Force-quit Vim (for when you've made changes but do not wish to save them)                                                              |
| Esc `i`                | Insert mode, allows you to type into the file                                                                                           |
| Esc `/cats`            | Searches your file for the nearest occurrence of the string "cats". Press `n` to go to the next occurrence or `N` to go to the previous |
| Esc `:set nu`          | Shows line numbers within your file                                                                                                     |
| Esc `:tabe <filepath>` | Opens the file at `filepath` in a new tab. You can use Tab for autocompletion                                                           |
| Esc `:tabn`            | Go to the next tab in the tab bar                                                                                                       |
| Esc `:tabp`            | Go to the previous tab in the tab bar                                                                                                   |

## 5， WSL复制文件

sudo cp /mnt/c/Users/Robert/Documents/GitHub/CS61C/fa22-lab-starter/tools/logisim-evolution.jar ./
