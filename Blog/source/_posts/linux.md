---
title: LINUX 随笔
date: 2021-11-15 17:35:33
tags:
    - 学习笔记
    - 技术
    - LINUX
categories: 
    - 笔记
    - GIT
cover: https://i.loli.net/2021/11/15/DX4gr8zZxJcnMRK.jpg
---
## 语法
#### 备份与还原备份
>  mysqldump -h 127.0.0.1 -uroot -p --all-databases > file_name.sql //备份 </br></br>
sz file_name.sql //下载备份⽂件 </br></br>
rz //上传备份⽂ </br></br>
mysql -h 127.0.0.1 -uroot -p < file_name.sql //选择⽂件 ,还原数据库备份

#### mv (文件移动更名)
文件改名:
> mv test.txt ttt.txt</br>

移动文件:
> mv ttt.txt test3


> 移动多个文件到指定目录
> mv -t test4/ test3/*</br>
 将文件1命名为文件2，如果文件2已存在，询问是否覆盖:
> mv -i 3.txt 1.txt</br></br>
> -b ：若需覆盖文件，则覆盖前先行备份。<br>
> -f ：force 强制的意思，如果目标文件已经存在，不会询问而直接覆盖；<br>
> -i ：若目标文件 (destination) 已经存在时，就会询问是否覆盖！<br>
> -u ：若目标文件已经存在，且 source 比较新，才会更新(update)<br>
> -t  ： --target-directory=DIRECTORY move all SOURCE arguments into<br> DIRECTORY，即指定mv的目标目录，该选项适用于移动多个源文件到一个目录的情况，此时目标目录在前，源文件在后。<br><br>

#### cp(文件复制)
文件/目录复制
 > 命令格式：cp [-adfilprsu] 源文件(source) 目标文件(destination)</br></br>
              cp [option] source1 source2 source3 ...  directory</br>
              
              
              
参数说明：
>    -a:是指archive的意思，也说是指复制所有的目录</br>
    -d:若源文件为连接文件(link file)，则复制连接文件属性而非文件本身</br>
    -f:强制(force)，若有重复或其它疑问时，不会询问用户，而强制复制</br>
    -i:若目标文件(destination)已存在，在覆盖时会先询问是否真的操作</br>
    -l:建立硬连接(hard link)的连接文件，而非复制文件本身</br>
    -p:与文件的属性一起复制，而非使用默认属性</br>
    -r:递归复制，用于目录的复制操作</br>
    -s:复制成符号连接文件(symbolic link)，即“快捷方式”文件</br>
    -u:若目标文件比源文件旧，更新目标文件</br>
    如将/test1目录下的file1复制到/test3目录，并将文件名改为file2,可输入以下命令：</br>
    cp /test1/file1 /test3/file2
    
#### rm(文件删除)

>   命令格式：rm [fir] 文件或目录</br>
    参数说明：</br>
    -f:强制删除</br>
    -i:交互模式，在删除前询问用户是否操作</br>
    -r:递归删除，常用在目录的删除</br>
    如删除/test目录下的file1文件，可以输入以下命令：</br>
    rm -i /test/file1
    
#### sz rz (文件上传与下载)
> rz   
选择文件进行上传</br>
>sz 文件名</br>
sz后面跟文件名可以进行文件从linux上面下载。

#### find(全局搜索)
将当前目录及其子目录下所有文件后缀为 .c 的文件列出来:

> find . -name "*.c"


将当前目录及其子目录中的所有文件列出：

> find . -type f


将当前目录及其子目录下所有最近 20 天内更新过的文件列出:

> find . -ctime -20


查找 /var/log 目录中更改时间在 7 日以前的普通文件，并在删除之前询问它们：

> find /var/log -type f -mtime +7 -ok rm {} \;


查找当前目录中文件属主具有读、写权限，并且文件所属组的用户和其他用户具有读权限的文件：

> find . -type f -perm 644 -exec ls -l {} \;


查找系统中所有文件长度为 0 的普通文件，并列出它们的完整路径：

> find / -type f -size 0 -exec ls -l {} \
----

#### cat、tac、tail、head(文件内容的查看)
##### 一、cat命令对文件内容正序查看时，可以使用cat命令。还可以两多个文件输出到一个文件中。也可以新建一个文件

> cat filename  正序查看文件所有内容</br></br>
  cat -n filename 带行号正序查看文件所有内容</br></br>
  cat -b filename 忽略空白行，带行号正序显示文件所有内容</br></br>
  cat  > filename 新建一个文件</br></br>
  cat filename1 filename2 > filename3 将filename1</br> filename2合并为filename3，此时filename3中只有filename1和filename2文件中的内容</br></br>
  cat filename1 filename2 >> filename3 将filename1</br></br> filename2文件的内容追加到filename3文件中</br></br>
  cat /dev/null > filename 清空filename文件中的内容</br></br>

##### 二、tac命令
tac倒过来就是cat，是将文件倒着显示，即文章最后一行显示在最上边。使用方法如下 tac filename

##### 三、tail命令

tail命令是指定显示文件后若干行的内容。下面介绍一下具体使用方法。

> tail -f filename 显示filename文件尾部内容，默认是10行，相当于tail -n 10，但是会不断刷新显示到屏幕上</br></br>
tail -n number filename 显示filename文件尾部number行内容</br></br>
tail -n +number filename 从第number行显示文件内容</br></br>

##### 四、head命令

> head 显示前n行的内容</br></br>
  head -n number filename


##### 文本关键字搜索

直接输入 /关键字 并回车，定位到第一个关键字，
> /content 通过n向下查找，通过N向上查找

直接输入 ?关键字 并回车
> ?content 通过n向上查找，通过N向下查找

##### 添加权限

给文件添加可执行权限指令
> chmod +x file  #file为文件名

给所有用户添加可读写执行权限
> chmod 777 file  #file为文件名

##### 查看进程 ps (Processes Status)

查看系统所有的java进程数据

> ps aux | grep java

##### 查看并杀死僵尸进程
> 用top 查看进程 如果zombie 大于“0”表示服务器当前存在僵尸进程

如果存在僵尸进程，可以使用命令
> ps -A -ostat,ppid,pid,cmd | grep -e '^\[Zz]\'

注解：
> -A 参数列出所有进程</br>
>-o 自定义输出字段 我们设定显示字段为 stat（状态）, ppid（进程父id）, pid(进程id)，cmd（命令）这四个参数
因为状态为 z或者Z的进程为僵尸进程，所以我们使用grep抓取stat状态为zZ进程

