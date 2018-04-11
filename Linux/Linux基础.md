**Linux与Windows的不同：**

* Linux 要区分大小写
* Linux 中所有内容都以文件形式保存，包括硬件
* Linux 不靠扩展名区分文件类型，但有约定俗成的扩展名：

```
压缩包："*.gz","*.bz2","*.tar.bz2","*.tgz"等
二进制软件包：".rpm"
网页文件："*.html", "*.php"
脚本文件："*.sh"
配置文件："*.conf"
```

* Windows 下的程序不能直接在Linux 中安装和运行

**字符界面的优势：**

* 占用的系统资源更少
* 减少出错、被攻击的可能

**常用命令：**

```
查询：ls -a 显示所有文件，包括隐藏
        -l 详细信息
        -d 目录属性
        -h 人性化显示文件大小
        -i 显示inode（ID号）
建立目录：mkdir -p 递归创建
创建文件：touch
删除：rmdir 删除空目录
     rm -rf 强制删除文件或目录
切换：cd 进入当前用户家目录（cd ~）
        cd - 进入上次目录
        cd .. 进入上一级目录
        cd . 进入当前目录
查询所在目录位置：pwd
复制：cp 复制文件
        -r 复制目录
        -p 连带文件属性
        -d 复制链接属性
        -a 相当于 -pdr（-p,-d,-r）
剪切或改名：mv（原文件和目标文件在同一目录就是改名，不在同一目录就是剪切）
链接命令: ln -s [原文件] [目标文件]
            -s 创建软连接
文件搜素：locate 在后台数据库按文件名搜索
            新建文件搜索不到因为数据库还没更新
            /var/lib/mlocate 就是locate命令所搜索的后台数据库
            updatedb 更新数据库，更新之后再搜索就能搜到
命令搜索命令：whereis 搜索命令所在路径及帮助文档所在位置
                -b 只查找可执行文件
                -m 只查找帮助文件
            which 搜索命令所在路径及别名
            echo $PATH PATH环境变量定义的是系统搜索命令的路径
文件搜索：find [搜索范围] [搜索条件]
        find / -name HelloWorld.class
                #应避免大范围搜索，会非常耗费系统资源
                #find是在系统当中搜索符合条件的文件名
                #如需匹配，使用通配符匹配，通配符是完全匹配
        Linux中的通配符：* 匹配任意内容
                        ? 任意一个字符
                        [] 任意一个中括号内的字符
        find /root -nouser 查找没有所有者的文件
        find /root -iname HelloWorld.class 不区分大小写
        find /var/log/ -mtime +10 查找10天前修改的文件
                        ctime 改变文件属性
                        atime 文件访问时间
                        -10 10天内修改的文件
                        10 10天当天修改的文件
        find . -inum 10229141 查找i节点是10229141的文件
        find . -size 25k 查找文件大小是25KB的文件（-25k：小于25KB，+：大于）
        find /etc -size +20k -a -size -50k 查找/etc/目录下大于20KB且小于50KB的文件
                             -o 逻辑或，两个条件满足一个即可
        find /etc -size +20k -a -size -50k -exec ls -lh {} \; ...并显示详细信息    
字符串搜索：grep -i 字符串 文件名  （-i:忽略大小写）
                #在文件当中匹配符合条件的字符串
               -v 排除指定字符串
帮助：man 命令  获取指定命令的帮助，如：man ls
        man -f 命令 查看命令拥有哪个级别的帮助（相当于whatis 命令）
        man -5 命令 获取指定命令的指定级别帮助
        man -k 命令 查看和命令相关的所有帮助（相当于apropos）
其他帮助：命令 --help 
        help shell内部命令 获取shell内部命令的帮助
        whereis cd 确定cd是否是shell内部命令
        help cd 获取内部命令cd的帮助
详细命令帮助：info 命令
                -回车：进入子帮助页面（带有*号标记）
                -u ：进入上层页面
                -n ：进入下一个帮助小节
                -p :进入上一个帮助小节
                -q ：退出
压缩：.zip  .gz  .bz2  .targz  .tar.bz2
        zip 压缩文件名 源文件 ：压缩文件
        zip -r 压缩文件名 源目录 ：压缩目录
        unzip 压缩文件 ：.zip格式解压缩
        移动或重命名文件或目录：
```


    ```
    mv [选项] 源文件或目录 目标文件或目录
        -b ：若需覆盖文件，则覆盖前先行备份。 
        -f ：force 强制的意思，如果目标文件已经存在，不会询问而直接覆盖；
        -i ：若目标文件 (destination) 已经存在时，就会询问是否覆盖！
        -u ：若目标文件已经存在，且 source 比较新，才会更新(update)
        -t  ： --target-directory=DIRECTORY move all SOURCE arguments into DIRECTORY
                即指定mv的目标目录，该选项适用于移动多个源文件到一个目录的情况，此时目标目录在前，源文件在后。
    ```

文件改名：

将文件 test.log 重命名为 test1.txt：

    ```
    mv test.log test1.txt
    ```
移动文件：

将 test1.txt 文件移到 test3 目录中

    ```
    mv test1.txt test3
    ```

将文件 log1.txt , log2.txt , log3.txt 移动到目录 test3 中：

将 log1.txt , log2.txt , log3.txt 三个文件移到 test3 目录中：

    ```
    mv log1.txt log2.txt log3.txt test3
    ```

又将三个文件移动到 test4 目录中：

    ```
    mv -t /opt/soft/test/test4/ log1.txt log2.txt log3.txt
    ```
目录的移动：

```
mv dir1 dir2

如果目录 dir2 不存在，将目录 dir1 改名为 dir2 ，否则，将 dir1 移动到 dir2 中
```
移动当前文件夹下的所有文件到上一级目录：**

    ```
    mv *../
    ```

把当前目录的一个子目录里的文件移动到另一个子目录里：

    ```
    mv test3/*.txt test5


**字符截取命令：sed**

* sed \[选项\] ‘\[动作\]’ 文件名

```
-n ：一般sed命令会把所有数据都输出到屏幕，加入此选项则只把经sed命令处理的行输出到屏幕
-e ：允许对输入数据应用多条sed命令编辑
-i ：用sed的修改结果直接修改读取数据的文件，而不是由屏幕输出
```

**Linux下WPS相关命令有：et** \(打开WPS表格\) , **wps** \(打开WPS文字程序\) , **wpp** \(打开WPS演示程序\)

```
1、不带操作对象参数
    et    //打开WPS表格程序
    wps    //打开WPS文字程序
    wpp    //打开WPS演示程序
2、带有操作对象参数
    et a.xls    //打开WPS表格程序，并编辑a.xls文档
    wps a.doc    //打开WPS文字程序，并编辑a.doc文档
    wpp a.ppt    //打开WPS演示程序，并编辑a.ppt文档
3、在后台运行
    nohup et a.xls &
    nohup wps a.doc &
    nohup wpp a.ppt &
```

**软连接和硬链接：**

| 硬链接 | 软连接 |
| :--- | :--- |
| 1. 拥有相同i节点和存储block块，可看作同一文件 | 1. 有自己的i节点和block块，数据块中只保存原文件的文件名和i节点号，没有实际文件数据 |
| 2. 可通过i节点识别 | 2. 类似Windows快捷方式 |
| 3. 不能跨分区 | 3. 修改任意文件，另一个都改变 |
| 4. 不能针对目录使用 | 4. 删除原文件，软连接不能使用 |

**常用目录的作用：**

```
/根目录
/bin 命令保存目录（普通用户就可读取的命令）
    /sbin 超级用户才能使用的目录
/boot 启动目录，启动相关文件
/dev 设备文件保存目录
/etc 配置文件保存目录
/home 普通用户的家目录
    /root 超级用户的家目录
/tmp 临时目录
/lib 系统库保存目录
/mnt 系统挂载目录
/media 挂载目录
/tmp 临时目录
/proc 直接写入内存的
/sys 同上
/usr 系统软件资源目录
    /usr/bin/系统命令（普通用户）
    /usr/sbin/系统命令（超级用户）
/var 系统相关文档内容
```



