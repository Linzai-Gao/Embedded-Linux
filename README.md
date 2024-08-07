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

### ls命令



