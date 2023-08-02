## 概论

shell是我们通过命令行与操作系统沟通的语言。

shell脚本可以直接在命令行中执行，也可以将一套逻辑组织成一个文件，方便复用。

AC Terminal中的命令行可以看成是一个“shell脚本在逐行执行”。

Linux中常见的shell脚本有很多种，常见的有：

```text
Bourne Shell(/usr/bin/sh或/bin/sh)
Bourne Again Shell(/bin/bash)
C Shell(/usr/bin/csh)
K Shell(/usr/bin/ksh)
zsh
…
```

Linux系统中一般默认使用bash，所以接下来讲解bash中的语法。

文件开头需要写#! /bin/bash，指明bash为脚本解释器。

## 学习技巧

不要死记硬背，遇到含糊不清的地方，可以在AC Terminal里实际运行一遍。

## 脚本示例

新建一个test.sh文件，内容如下：

```bash
#! /bin/bash
echo "Hello World!"
```

## 运行方式

作为可执行文件

```bash
acs@9e0ebfcd82d7:~$ chmod +x test.sh  # 使脚本具有可执行权限
acs@9e0ebfcd82d7:~$ ./test.sh  # 当前路径下执行
Hello World!  # 脚本输出
acs@9e0ebfcd82d7:~$ /home/acs/test.sh  # 绝对路径下执行
Hello World!  # 脚本输出
acs@9e0ebfcd82d7:~$ ~/test.sh  # 家目录路径下执行
Hello World!  # 脚本输出
```

用解释器执行

```bash
acs@9e0ebfcd82d7:~$ bash test.sh
Hello World!  # 脚本输出
```

# 注释

## 单行注释

每行中#之后的内容均是注释。

```bash
# 这是一行注释
echo 'Hello World'  #  这也是注释
```

## 多行注释

格式：

```bash
:<<EOF
第一行注释
第二行注释
第三行注释
EOF
```

其中EOF可以换成其它任意字符串。例如：

```bash
:<<abc
第一行注释
第二行注释
第三行注释
abc

:<<!
第一行注释
第二行注释
第三行注释
!
```

# 变量

## 定义变量

定义变量，不需要加\$符号，例如：

```bash
name1='yxc'  # 单引号定义字符串
name2="yxc"  # 双引号定义字符串
name3=yxc    # 也可以不加引号，同样表示字符串
```

## 使用变量

使用变量，需要加上\$符号，或者\${}符号。花括号是可选的，主要为了帮助解释器识别变量边界。

```bash
name=yxc
echo $name  # 输出yxc
echo ${name}  # 输出yxc
echo ${name}acwing  # 输出yxcacwing
```

## 只读变量

使用readonly或者declare可以将变量变为只读。

```bash
name=yxc
readonly name
declare -r name  # 两种写法均可

name=abc  # 会报错，因为此时name只读
```

## 删除变量

unset可以删除变量。

```bash
name=yxc
unset name
echo $name  # 输出空行
```

## 变量类型

自定义变量（局部变量）

+ 子进程不能访问的变量

环境变量（全局变量）

+ 子进程可以访问的变量

自定义变量改成环境变量：

```bash
acs@9e0ebfcd82d7:~$ name=yxc  # 定义变量
acs@9e0ebfcd82d7:~$ export name  # 第一种方法
acs@9e0ebfcd82d7:~$ declare -x name  # 第二种方法
```

环境变量改为自定义变量：

```bash
acs@9e0ebfcd82d7:~$ export name=yxc  # 定义环境变量
acs@9e0ebfcd82d7:~$ declare +x name  # 改为自定义变量
```

## 字符串

字符串可以用单引号，也可以用双引号，也可以不用引号。

单引号与双引号的区别：

>单引号中的内容会原样输出，不会执行、不会取变量；
>
>双引号中的内容可以执行、可以取变量；

```bash
name=yxc  # 不用引号
echo 'hello, $name \"hh\"'  # 单引号字符串，输出 hello, $name \"hh\"
echo "hello, $name \"hh\""  # 双引号字符串，输出 hello, yxc "hh"
```

获取字符串长度

```bash
name="yxc"
echo ${#name}  # 输出3
```

提取子串

```bash
name="hello, yxc"
echo ${name:0:5}  # 提取从0开始的5个字符
```

# 默认变量

## 文件参数变量

在执行shell脚本时，可以向脚本传递参数。\$1是第一个参数，\$2是第二个参数，以此类推。特殊的，\$0是文件名（包含路径）。例如：

创建文件test\.sh:

#! /bin/bash

echo "文件名："$0
echo "第一个参数："$1
echo "第二个参数："$2
echo "第三个参数："$3
echo "第四个参数："$4
然后执行该脚本：

acs@9e0ebfcd82d7:~$ chmod +x test.sh 
acs@9e0ebfcd82d7:~$ ./test.sh 1 2 3 4
文件名：./test.sh
第一个参数：1
第二个参数：2
第三个参数：3
第四个参数：4
其它参数相关变量

作者：yxc
链接：https://www.acwing.com/blog/content/9691/
来源：AcWing
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。