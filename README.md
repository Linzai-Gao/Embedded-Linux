# 嵌入式Linux学习

## 1.vim编辑器的使用

### 1.1如何打开

通过在对应的路径终端下输入命令“vi+文件名”即可，1.如果该文件存在，则打开 2.此文件不存在，自动创建。

### 1.2三种模式

#### 1.一般模式

打开vim后即为一般模式

#### 2.编辑模式

我们可以输入a,i,或者o进入编辑模式，观察光标会向后移一位

#### 3.命令行模式

我们输入：冒号，或者/,?斜杠，问号都可进入命令行模式

:set number显示行数

### 1.3各种功能

#### 1.移动光标

在一般模式下，可以通过上下左右键进行，或者K,J,H,L进行移动

K：向上移动

J：向下移动

H：向左移动

L：向右移动

#### 2.快速定位

在一般模式下，双击g，将光标定位到第一行

单击大写的G，跳转到最后一行

输入ngg，跳转到指定的n行

#### 3.复制粘贴

1.先将光标放在需要复制的行首然后按下v，用上下左右键进行选择需要复制的文本等，选择好了后按下Y，后面在我们需要粘贴的地方按下p

2.(快捷)，光标在需要复制的那一行然后按下yy，进行复制，再在需要粘贴的地方按下p

yy：复制当前行

nyy：复制当前行下n行

#### 4.删除

方法一：编辑模式，使用delete删除

方法二：使用dd命令

dd：删除光标所在行

ndd：删除n行

n1,n2d：删除指定范围的行，在**命令行**下操作。

#### 5.撤销

使用字母u来进行撤销，反撤销是ctrl+r。

#### 6.查找

在**命令行**下我们输入/或者?来查找

/：斜杠是**向下查找**再按下n键进行下一个

?：问号是**向上查找**再按下b键进行下一个

#### 7.保存

:q!  强行退出

:wq 保存退出

:q 退出没有编辑过的文本

## 2.Linux常用命令

### 2.1 ls 命令

**ls命令功能：查看文件信息**，打开虚拟机进入终端，输入ls就会列出路径所有文件。

![image-20240808112056554](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20240808112056554.png)

很多文件隐藏无法查看，需要加上在后面参数

文件名前面有.则为隐藏文件，如.bash_history

#### 参数

**`ls -a`：显示所有文件(包括隐藏文件)**

**`ls -l`：显示文件详细信息**

![image-20240808112255729](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20240808112255729.png)

#### 文件类型和权限

**第一列中的第一位d和-代表了这个文件的类型**

第一个参数：

d：目录文件，

-：普通文件，

p：管理文件，

l：链接文件，

b：块设备文件，

c：字符设备文件，

s：套接字文件

**第一列第一个参数后面的代表了用户权限**

r：可读权限，

w：可写权限，

x：可执行权限，

-：没有权限

#### 其余列

**第二列**

在-开头的普通文件下，其表示链接数，相当于快捷方式。

在d开头的目录文件下，其表示子目录数(不是文件数)。

**第三第四列**

是用户名和组名

**第五列**

是文件大小，字节为单位

**第六列**

修改时间

**最后**

文件名，

.表示当前目录，..表示上一级目录

### 2.2 cd 命令

**cd命令功能：目录切换**

```shell
cd+空格+路径//切换到指定路径
cd ..//进入上一级路径
//然后ls列出当下文件
cd linzaii/
//进入指定路径
```

**小提示，在cd 后写出首字母然后按下tab会自动补全**

![image-20240808114335365](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20240808114335365.png)

```shell
cd / //进入根目录
cd ~ //进入家目录
//在root用户下的家目录和普通用户不同
```

![image-20240808115319701](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20240808115319701.png)

### 2.3 pwd 命令

**pwd命令：显示当前路径**

![image-20240808114645335](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20240808114645335.png)

### 2.4 mkdir 命令

**功能：创建一个新的文件夹**

```shell
mkdir test//在家目录下创建一个文件夹
mkdir -p//创建多级目录（相对路径）
```

![image-20240809134642309](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20240809134642309.png)

### 2.5 rmdir 命令

**功能：删除一个*空目录***（无法删除有东西的文件夹）

![image-20240809135037132](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20240809135037132.png)

### 2.6 rm 命令

**功能：删除文件或目录**

**注意：删除目录一定要加上-r参数**

**这个命令有三个常用参数：-r -f -i**

```shell
rm -r test/
//递归删除这个目录下的所有文件
rm -ri test/
//在删除之前进行询问
rm -f //强制删除
```

![image-20240816154309836](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20240816154309836.png)

### 2.7 touch 命令

**功能：创建一个**文件(mkdir是创建新的文件夹)

```shell
touch test.c
//创建test.c文件
rm test.c
//test.c只是文件而不是文件夹，不用-r但是可以使用-f和-i
```

### 2.8 clear 命令

**功能：刷新屏幕但是会保留历史记录(清屏命令)**

### 2.9 reset 命令

**功能：清屏，但不保留历史记录**

### 2.10 cp 命令

**功能：复制文件或者复制目录**

#### 2.10.1复制文件

```shell
cp 源文件 目标文件
cp test1.c test2.c
//将test1.c复制到test2.c
```

![image-20240816155953526](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20240816155953526.png)

```shell
//将文件复制到指定路径
cp 源文件 路径
```

现在我们位于/home/linzaii路径下，我们要将test1.c文件复制到/home下

```shell
cp test1.c ..
//提示没有足够的权限
sudo cp test1.c ..
//或者直接 su root进入root模式
```

![image-20240816160404620](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20240816160404620.png)

#### 2.10.2复制文件夹(目录)

**复制目录需要加上-r参数**表示**递归复制**

```shell
cp -r 原目录 路径
cp -r test test1
sudo cp -r test ..
//将test复制到上一路径
```

![image-20240816161045578](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20240816161045578.png)

![image-20240816161304416](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20240816161304416.png)

### 2.11 mv 命令

**功能：修改文件和文件夹名称，移动文件**

#### 2.11.1修改名称

```shell
mv 原文件名称 修改后的名称
mv test1.c test3.c
mv test1 test3
```

![image-20240816161927796](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20240816161927796.png)

#### 2.11.2移动文件

先在test3中创建一个文件lin.c，然后通过mv命令将它移动到上一级路径/home/linzaii

```shell
//在test3中
mv lin.c ..
//更换到上一路径
cd ..
//移动回去
mv lin.c ./test3
```

![image-20240816163054113](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20240816163054113.png)

#### **如果要移动多个文件呢**

使用*通配符，也就是任意

比如test3下有多个文件lin.c和lin1.c

将这两个文件移动到上一路径中

```shell
//在test3路径中
mv * ..
cd ..
ls
```

![image-20240816163512571](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20240816163512571.png)

### 2.12 tar 命令

**功能：对文件和目录进行压缩和解压缩**

#### 常用参数

-c：创建一个压缩文件

-x：对压缩文件进行解压缩

-z：gzip格式进行压缩或解压缩，后缀*tar.gz*

-j：bzip2格式进行压缩或解压缩，后缀*tar.bz2*

-f：表示要操作的文件，一般放在参数最后，后面接上文件名称

-v：显示正在进行操作的文件

-C：后面加上路径，即解压到指定路径

#### 2.12.1 gzip格式

```shell
//先在test3文件夹路径下，进行打包操作
tar -czvf test.tar.gzip lin.c
//然后解压缩到上一路径
tar -xzf test.tar.gzip -C ..
```

![image-20240816201654024](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20240816201654024.png)



### 2.13 ifconfig 命令
