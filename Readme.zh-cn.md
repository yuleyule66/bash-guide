>原文地址：https://github.com/Idnan/bash-guide   
>翻译：[杨晓东(Savorboard)](http://savorboard.cnblogs.com) 

<p align="center">
  <img src="https://cloud.githubusercontent.com/assets/2059754/24601246/753a7f36-1858-11e7-9d6b-7a0e64fb27f7.png" alt="bash logo"/>
</p>

## 目录

  1. [基本操作](#basic-operations)  
    1.1. [文件操作](#file-operations)  
    1.2. [文本操作](#text-operations)  
    1.3. [目录操作](#directory-operations)  
    1.4. [SSH, 系统信息 & 网络操作](#ssh-system-info-network-operations)  
  2. [基本 Shell 编程](#basic-shell-programming)  
    2.1. [变量](#variables)  
    2.2. [字符串替换](#string-substitution)  
    2.3. [函数](#functions)  
    2.4. [条件](#conditionals)  
    2.5. [循环](#loops)  
  3. [技巧](#tricks)  
  4. [调试](#debugging)  
  
## 1. Basic Operations

#### a. `export`
显示所有的环境变量，如果你想获取某个变量的详细信息，使用 `echo $VARIABLE_NAME`.  
```bash
export
```
Example:
```bash
$ export
SHELL=/bin/zsh
AWS_HOME=/Users/adnanadnan/.aws
LANG=en_US.UTF-8
LC_CTYPE=en_US.UTF-8
LESS=-R

$ echo $SHELL
/usr/bin/zsh
```

#### b. `whereis`
whereis使用系统自动构建的数据库来搜索可执行文件，源文件和手册页面。
```bash
whereis name
```
Example:
```bash
$ whereis php
/usr/bin/php
```

#### c. `which`
它在环境变量PATH指定的目录中搜索可执行文件。此命令将打印可执行文件的完整路径。
```bash
which program_name 
```
Example:
```bash
$ which php
/c/xampp/php/php
```

#### d. clear
清除窗口上的内容。

### 1.1. File Operations
<table>
   <tr>
      <td><a href="#a.-ls">ls</a></td>
      <td><a href="#b.-touch">touch</a></td>
      <td><a href="#c.-cat">cat</a></td>
      <td><a href="#d.-more">more</a></td>
      <td><a href="#e.-head">head</a></td>
      <td><a href="#f.-tail">tail</a></td>
      <td><a href="#g.-mv">mv</a></td>
      <td><a href="#h.-cp">cp</a></td>
      <td><a href="#i.-rm">rm</a></td>
      <td><a href="#j.-diff">diff</a></td>
   </tr>
   <tr>
      <td><a href="#k.-chmod">chmod</a></td>
      <td><a href="#l.-gzip">gzip</a></td>
      <td><a href="#m.-gunzip">gunzip</a></td>
      <td><a href="#n.-gzcat">gzcat</a></td>
      <td><a href="#o.-lpr">lpr</a></td>
      <td><a href="#p.-lpq">lpq</a></td>
      <td><a href="#q.-lprm">lprm</a></td>
   </tr>
</table>

#### a. `ls`
列出您的文件。`ls`有很多选项：`-l`列出“长格式”的文件，其中包含文件的确切大小，拥有该文件的人员，有权查看该文件，以及何时进行上次修改。`-a`列出所有文件，包括隐藏文件。有关此命令的更多信息，请检查此[链接](https://ss64.com/bash/ls.html)。
```bash
ls option
```
Example:
```
$ ls -al
rwxr-xr-x   33 adnan  staff    1122 Mar 27 18:44 .
drwxrwxrwx  60 adnan  staff    2040 Mar 21 15:06 ..
-rw-r--r--@  1 adnan  staff   14340 Mar 23 15:05 .DS_Store
-rw-r--r--   1 adnan  staff     157 Mar 25 18:08 .bumpversion.cfg
-rw-r--r--   1 adnan  staff    6515 Mar 25 18:08 .config.ini
-rw-r--r--   1 adnan  staff    5805 Mar 27 18:44 .config.override.ini
drwxr-xr-x  17 adnan  staff     578 Mar 27 23:36 .git
-rwxr-xr-x   1 adnan  staff    2702 Mar 25 18:08 .gitignore
```

#### b. `touch`
创建或更新您的文件。 
```bash
touch filename
```
Example:
```bash
$ touch trick.md
```

#### c. `cat`
它可以在UNIX或Linux下用于以下目的。

* 在屏幕上显示文本文件
* 复制文本文件
* 合并文本文件
* 创建新的文本文件

```bash
cat filename
cat file1 file2 
cat file1 file2 > newcombinedfile
```

#### d. `more`
显示文件的第一部分（用空格移动并键入q以退出）。
```bash
more filename
```

#### e. `head`
输出文件的前10行。
```bash
head filename
```

#### f. `tail`
输出最后10行文件。用于-f在文件增长时输出附加数据。 
```bash
tail filename
```


#### g. `mv`
将文件从一个位置移动到另一个位置。  
```bash
mv filename1 filename2
```
`filename1` 文件的源路径，`filename2` 是目标路径。

#### h. `cp`
将文件从一个位置复制到另一个位置。   
```bash
cp filename1 filename2
```
`filename1` 文件的源路径，`filename2` 是目标路径。

#### i. `rm`

删除文件。在目录上使用此命令会给您显示一个错误： `rm: directory: is a directory`。 为了删除目录，你必须传递`-rf`去递归删除目录中的所有内容。

```bash
rm filename
```

#### j. `diff`
比较文件，并列出他们的差异。

```bash
diff filename1 filename2
```

#### k. `chmod`
让您更改文件的读取，写入和执行权限。
```bash
chmod -options filename
```

#### l. `gzip`
压缩文件。
```bash
gzip filename
```

#### m. `gunzip`
解压缩gzip压缩的文件。
```bash
gunzip filename
```

#### n. `gzcat`
让你查看gzip压缩文件，而不需要gunzip它。
```bash
gzcat filename
```

#### o. `lpr`
打印文件。 
```bash
lpr filename
```

#### p. `lpq`
查看打印机队列。 
```bash
lpq
```
Example:
```bash
$ lpq
Rank    Owner   Job     File(s)                         Total Size
active  adnanad 59      demo                            399360 bytes
1st     adnanad 60      (stdin)                         0 bytes
```

#### q. `lprm`
从打印队列移除某些内容。
```bash
lprm jobnumber
```

### 1.2. Text Operations

<table>
   <tr>
      <td><a href="#a.-awk">awk</a></td>
      <td><a href="#b.-grep">grep</a></td>
      <td><a href="#c.-wc">wc</a></td>
      <td><a href="#d.-sed">sed</a></td>
      <td><a href="#e.-sort">sort</a></td>
      <td><a href="#f.-uniq">uniq</a></td>
      <td><a href="#g.-cut">cut</a></td>
      <td><a href="#h.-echo">echo</a></td>
      <td><a href="#i.-fmt">fmt</a></td>
   </tr>
   <tr>
      <td><a href="#j.-tr">tr</a></td>
      <td><a href="#k.-nl">nl</a></td>
      <td><a href="#l.-egrep">egrep</a></td>
      <td><a href="#m.-fgrep">fgrep</a></td>
   </tr>
</table>

#### a. `awk`
awk是处理文本文件最有用的命令。它一行一行地在整个文件上运行。默认情况下，它使用空格分隔字段。awk命令最常用的语法是
```bash
awk '/search_pattern/ { action_to_take_if_pattern_matches; }' file_to_parse
```
让我们采取以下文件 `/etc/passwd`。以下是此文件包含的示例数据：

```
root:x:0:0:root:/root:/usr/bin/zsh
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
```
所以现在让我们从这个文件只获取用户名。 `-F` 指定在我们要基于哪个分隔字段。在我们的例子中 `:` 。`{ print $1 }` 意味着打印出第一个匹配字段。
```bash
awk -F':' '{ print $1 }' /etc/passwd
```
运行上述命令后，您将获得以下输出。
```
root
daemon
bin
sys
sync
```
有关如何使用`awk`的更多细节，请查看以下[链接](https://www.cyberciti.biz/faq/bash-scripting-using-awk)。

#### b. `grep`
查找文件内的文本。您可以使用grep搜索与一个或多个正则表达式匹配的文本行，并仅输出匹配的行。

```bash
grep pattern filename
```
Example:
```bash
$ grep admin /etc/passwd
_kadmin_admin:*:218:-2:Kerberos Admin Service:/var/empty:/usr/bin/false
_kadmin_changepw:*:219:-2:Kerberos Change Password Service:/var/empty:/usr/bin/false
_krb_kadmin:*:231:-2:Open Directory Kerberos Admin Service:/var/empty:/usr/bin/false
```
您还可以通过使用`-i`选项强制grep忽略单词大小写。`-r`可用于搜索指定目录下的所有文件，例如：
```bash
$ grep -r admin /etc/
```
`-w` 只搜索单词。有关`grep`详细信息，请查看以下[链接](https://www.cyberciti.biz/faq/grep-in-bash)。

#### c. `wc`
告诉你一个文件中有多少行，多少单词和多少字符。

```bash
wc filename
```
Example:
```bash
$ wc demo.txt
7459   15915  398400 demo.txt
```
`7459` 是行数, `15915` 是单词数， `398400` 是字符数.

#### d. `sed`
用于过滤和转换文本的流编辑器。

*example.txt*
```bash
Hello This is a Test 1 2 3 4
``` 

*用连字符替换所有空格*
```bash
sed 's/ /-/g' example.txt
```
```bash
Hello-This-is-a-Test-1-2-3-4
```

*使用"d"替换所有的数字*
```bash
sed 's/[0-9]/d/g' example.txt
```
```bash
Hello This is a Test d d d d
```

#### e. `sort`
排序文本文件的行

*example.txt*
```bash
f
b
c
g
a
e
d
```

*sort example.txt*
```bash
sort example.txt
```
```bash
a
b
c
d
e
f
g
```

*随机化一个排序的example.txt*
```bash
sort example.txt | sort -R
```
```bash
b
f
a
c
d
g
e
```

#### f. `uniq`
报告或省略重复的行

*example.txt*
```bash
a
a
b
a
b
c
d
c
```

*只显示example.txt的唯一行（首先你需要排序，否则看不到重叠）*
```bash
sort example.txt | uniq
```
```bash
a
b
c
d
```

*显示每行的唯一项，并告诉我找到了多少个实例*
```bash
sort example.txt | uniq -c
```
```bash
    3 a
    2 b
    2 c
    1 d
```

#### g. `cut`
从每行文件中删除部分。

*example.txt*
```bash
red riding hood went to the park to play
```

*显示第2,7和9栏的空格作为分隔符*
```bash
cut -d " " -f2,7,9 example.txt
```
```bash
riding park play
```

#### h. `echo`

显示一行文字

*显示 "Hello World"*
```bash
echo Hello World
```
```bash
Hello World
```

*用字母之间的换行显示 "Hello World"*
```bash
echo -ne "Hello\nWorld\n"
```
```bash
Hello
World
```

#### i. `fmt`
简单的最佳文本格式化程序

*example: example.txt (1 line)*
```bash
Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.
```

*将example.txt的行输出为20个字符的宽度*
```bash
cat example.txt | fmt -w 20
```
```bash
Lorem ipsum
dolor sit amet,
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

#### j. `tr`

翻译或删除字符

*example.txt*
```bash
Hello World Foo Bar Baz!
```

*把所有小写字母变成为大写*
```bash
cat example.txt | tr 'a-z' 'A-Z' 
```
```bash
HELLO WORLD FOO BAR BAZ!
```

*把所有的空格变成换行符*
```bash
cat example.txt | tr ' ' '\n'
```
```bash
Hello
World
Foo
Bar
Baz!
```

#### k. `nl`

显示文件的行数

*example.txt*
```bash
Lorem ipsum
dolor sit amet,
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

*带行号显示 example.txt*
```bash
nl -s". " example.txt 
```
```bash
     1. Lorem ipsum
     2. dolor sit amet,
     3. consetetur
     4. sadipscing elitr,
     5. sed diam nonumy
     6. eirmod tempor
     7. invidunt ut labore
     8. et dolore magna
     9. aliquyam erat, sed
    10. diam voluptua. At
    11. vero eos et
    12. accusam et justo
    13. duo dolores et ea
    14. rebum. Stet clita
    15. kasd gubergren,
    16. no sea takimata
    17. sanctus est Lorem
    18. ipsum dolor sit
    19. amet.
```

#### l. `egrep`
打印匹配模式的行 - 扩展表达式（别名为：'grep -E'）

*example.txt*
```bash
Lorem ipsum
dolor sit amet, 
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

*在其中显示“Lorem”或“dolor”的行*
```bash
egrep '(Lorem|dolor)' example.txt
or
grep -E '(Lorem|dolor)' example.txt
```
```bash
Lorem ipsum
dolor sit amet,
et dolore magna
duo dolores et ea
sanctus est Lorem
ipsum dolor sit
```

#### m. `fgrep`
打印匹配模式到的行 - FIXED模式匹配（别名为：'grep -F'）
*example.txt*
```bash
Lorem ipsum
dolor sit amet,
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
foo (Lorem|dolor) 
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

*在example.txt中找到具体的字符串'（Lorem | doloar）'*
```bash
fgrep '(Lorem|dolor)' example.txt
or
grep -F '(Lorem|dolor)' example.txt
```
```bash
foo (Lorem|dolor) 
```

### 1.3. Directory Operations

<table>
   <tr>
      <td><a href="#a.-mkdir">mkdir</a></td>
      <td><a href="#b.-cd">cd</a></td>
      <td><a href="#c.-pwd">pwd</a></td>
   </tr>
</table>

#### a. `mkdir`
生成一个新的目录。
```bash
mkdir dirname
```

#### b. `cd`
执行这个，从一个目录转移到另外一个目录。
```bash
$ cd
```
将你移动到主目录。此命令接受可选的`dirname`，将你移动到该目录。
```bash
cd dirname
```

#### c. `pwd`
告诉你你目前所在的目录。
```bash
pwd
```

### 1.4. SSH, System Info & Network Operations

<table>
   <tr>
      <td><a href="#a.-ssh">ssh</a></td>
      <td><a href="#b.-whoami">whoami</a></td>
      <td><a href="#c.-passwd">passwd</a></td>
      <td><a href="#d.-quota">quota</a></td>
      <td><a href="#e.-date">date</a></td>
      <td><a href="#f.-cal">cal</a></td>
      <td><a href="#g.-uptime">uptime</a></td>
      <td><a href="#h.-w">w</a></td>
      <td><a href="#i.-finger">finger</a></td>
      <td><a href="#j.-uname">uname</a></td>
   </tr>
   <tr>
      <td><a href="#k.-man">man</a></td>
      <td><a href="#l.-df">df</a></td>
      <td><a href="#m.-du">du</a></td>
      <td><a href="#n.-last">last</a></td>
      <td><a href="#o.-ps">ps</a></td>
      <td><a href="#p.-kill">kill</a></td>
      <td><a href="#q.-killall">killall</a></td>
      <td><a href="#r.-top">top</a></td>
      <td><a href="#s.-bg">bg</a></td>
      <td><a href="#t.-fg">fg</a></td>
   </tr>
   <tr>
      <td><a href="#u.-ping">ping</a></td>
      <td><a href="#v.-whois">whois</a></td>
      <td><a href="#w.-dig">dig</a></td>
      <td><a href="#x.-wget">wget</a></td>
      <td><a href="#y.-scp">scp</a></td>
   </tr>
</table>

#### a. `ssh`
ssh (SSH client) 是一个用来在登录到远程机器并执行的命令的程序。
```bash
ssh user@host
```
此命令还接受`-p`可用于连接到特定端口的选项。
```bash
ssh -p port user@host
```

#### b. `whoami`

返回当前登录用户名。

#### c. `passwd`

允许当前登录的用户更改其密码。

#### d. `quota`

显示您的磁盘配额。

```bash
quota -v
```

#### e. `date`
显示当前日期和时间。

#### f. `cal`
显示月份的日历。

#### g. `uptime`
显示当前的正常运行时间。

#### h. `w`
显示谁在线

#### i. `finger`
Displays information about user.  
```bash
finger username
```

#### j. `uname`
显示内核信息。
```bash
uname -a
```

#### k. `man`
显示指定命令的手册。  
```bash
man command
```

#### l. `df`
显示磁盘使用情况。

#### m. `du`
显示文件名中文件和目录的磁盘使用情况（du -s只给出一个总数）。

```bash
du filename
```

#### n. `last`
列出您最后登录的指定用户。 
```bash
last yourUsername
```

#### o. `ps`
列出您的进程。
```bash
ps -u yourusername
```

#### p. `kill`
使用您所提供的ID杀死（结束）进程。
```bash
kill PID
```

#### q. `killall`
用名称杀死所有进程。
```bash
killall processname
```

#### r. `top`
显示当前活动的进程。

#### s. `bg`
列出停止的或后台工作的Job; 恢复在后台停止的Job。

#### t. `fg`
前台化最近的Job。
Brings the most recent job in the foreground.

#### u. `ping`
Pings主机并输出结果。
```bash
ping host
```

#### v. `whois`
获取域的whois信息。
```bash
whois domain
```

#### w. `dig`
获取域的DNS信息。 
```bash
dig domain
```

#### x. `wget`
下载文件。 
```bash
wget file
```


#### y. `scp`
在本地主机和远程主机之间或两台远程主机之间传输文件。

*从本地主机复制到远程主机*
```bash
scp source_file user@host:directory/target_file
```
*从远程主机复制到本地主机*
```bash
scp user@host:directory/source_file target_file
scp -r user@host:directory/source_folder farget_folder
```
此命令还接受`-P`选项可用于连接到特定的端口。  
```bash
scp -P port user@host:directory/source_file target_file
```


## 2. Basic Shell Programming

在bash中你将编写第一行脚本文件，被叫做`shebang`。任何脚本中的这一行来确定脚本的执行能力，如独立的可执行文件，而不是在终端中预先键入sh，bash，python，php等。

```bash
#!/bin/bash
```

### 2.1. Variables

在bash中创建变量与其他语言类似。没有数据类型。bash中的变量可以包含数字，字符，字符串等。您无需声明变量，只需为其引用分配一个值即可创建它。

Example:
```bash
str="hello world"
```

上面的一行创建一个变量str并给它赋值“hello world”。通过`$`放在变量名的开头来检索变量的值。

Example:
```bash
echo $str   # hello world
```
像其他语言一样，bash也有数组。数组是包含多个值的变量。数组的大小没有最大限制。bash中的数组为零。第一个元素被索引为元素0.在bash中创建数组有几种方法。以下给出了哪些。

Examples:
```bash
array[0] = val
array[1] = val
array[2] = val
array=([2]=val [0]=val [1]=val)
array(val val val)
```
要在特定索引处显示值，请使用以下语法：

```bash
${array[i]}     # where i is the index
```

如果没有提供索引，则假定为数组元素0。要了解数组中有多少值，请使用以下语法：

```bash
${#array[@]}
```

Bash也支持三元条件。下面是一些例子。

```bash
${varname:-word}    # 如果varname存在且不为null，则返回其值; 否则返回word
${varname:=word}    # 如果varname存在且不为null，则返回其值;否则设置它，然后返回其值
${varname:+word}    # 如果varname存在并且不为null，返回word; 否则返回null 
${varname:offset:length}    # 执行子字符串扩展。它返回$ varname的子字符串，从offset开始，最多为length的字符
```

### 2.2 String Substitution

检查一些关于如何操作字符串的语法

```bash
${variable#pattern}         # if the pattern matches the beginning of the variable's value, delete the shortest part that matches and return the rest
${variable##pattern}        # if the pattern matches the beginning of the variable's value, delete the longest part that matches and return the rest
${variable%pattern}         # if the pattern matches the end of the variable's value, delete the shortest part that matches and return the rest
${variable%%pattern}        # if the pattern matches the end of the variable's value, delete the longest part that matches and return the rest
${variable/pattern/string}  # the longest match to pattern in variable is replaced by string. Only the first match is replaced
${variable//pattern/string} # the longest match to pattern in variable is replaced by string. All matches are replaced
${#varname}     # returns the length of the value of the variable as a character string
```

### 2.3. Functions

几乎与任何编程语言一样，您可以使用函数以更逻辑的方式对代码段进行分组，或者实践递归的神圣艺术。声明函数只是编写函数my_func {my_code}的问题。调用一个函数就像调用另一个程序一样，你只需要写上它的名字。

```bash
functname() {
    shell commands
}
```

Example:
```bash
#!/bin/bash
function hello {
   echo world!
}
hello

function say {
    echo $1
}
say "hello world!"
```

当您运行上述示例时，该hello函数将输出“world！”。上述两个功能`hello`和`say`是相同的。主要区别是功能`say`。此功能打印其接收到的第一个参数。函数内的参数以与给脚本的参数相同的方式进行处理。


### 2.4. Conditionals

bash中的条件语句与其他编程语言相似。条件有许多形式，如最基本的形式是`if`表达式`then`语句，其中语句只有在表达式为真时执行。

```bash
if [expression]; then
    will execute only if expression is true
else
    will execute if expression is false
fi
```
有时，如果条件变得混乱，所以你可以使用相同的条件`case statements`。 

```bash
case expression in
    pattern1 )
        statements ;;
    pattern2 )
        statements ;;
    ...
esac
```

Expression Examples:

```bash
statement1 && statement2  # 两边的条件都为true
statement1 || statement2  # 其中一边为true

str1=str2       # str1 匹配 str2
str1!=str2      # str1 不匹配 str2
str1<str2       # str1 是否小于 str2
str1>str2       # str1 是否大于 str2
-n str1         # str1 不为空(长度大于 0)
-z str1         # str1 为空(长度为 0)

-a file         # 文件存在 
-d file         # 文件存在，是一个目录 
-e file         # 文件存在; 相同的-a 
-f file         # 文件存在，是一个常规文件（即不是目录或其他特殊类型的文件） 
-r file         # 你有读权限 
-r file         # 文件存在，不为空 
-w file         # 你有写权限 
-x file         # 你有文件的执行权限

file1 -nt file2     # file1 is newer than file2
file1 -ot file2     # file1 is older than file2

-lt     # 小于 
-le     # 小于或等于 
-eq     # 等于
-ge     # 大于或等于 
-gt     # 大于
-ne     # 不等于
```

### 2.5. Loops

bash 中有三种不同类型的循环。 `for`, `while` 和 `until`.

 `for` 语法:
```bash
for x := 1 to 10 do
begin
  statements
end

for name [in list]
do
  statements that can use $name
done

for (( initialisation ; ending condition ; update ))
do
  statements...
done
```

`while` 语法:
```bash
while condition; do
  statements
done
```

`until` 语法:
```bash
until condition; do
  statements
done
```

## 3. Tricks

#### 设置一个别名
`bash_profile` 可以通过运行后面的命令打开。 `nano ~/.bash_profile`

> alias dockerlogin='ssh www-data@adnan.local -p2222'  # add your alias in .bash_profile

#### 快速去特定的目录
nano ~/.bashrc
> export hotellogs="/workspace/hotel-api/storage/logs"

source ~/.bashrc
cd hotellogs


## 4. Debugging

您可以通过传递不同的选项来轻松地调试bash脚本bash。例如-n，不会运行命令并仅检查语法错误。-vecho命令在运行它们之前。-x命令行处理后的echo命令。


```bash
bash -n scriptname
bash -v scriptname
bash -x scriptname
```

## License

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
