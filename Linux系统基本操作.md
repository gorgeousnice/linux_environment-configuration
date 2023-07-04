# Linux系统学习

##常用命令：

挂在后台跑：













## 1、folder&files

1、显示当前的工作目录：

```r
(base) gorgeous@192 ~ %
#查看当前路径
pwd #print work direcory
##/Users/gorgeous 返回绝对路径
```

2、mkdir（make directory）创建文件夹(工作目录)

```r
#在当前目录下创建文件夹
mkdir teat
#在当前目录下一次性创建a<b<c<d的多层文件目录
mkdir -p a/b/c/d
```

3、cd（change diractory）修改工作目录

```R
# 进入根目录下的tmp目录
cd /tmp 
# 回到家目录
cd
# 进入上一级目录
cd ..
# 返回上一次离开的目录
cd -
```

4、ls（list）查看目录/文件夹里面的内容

```R
# 以列方式列出当前目录下的文件和子目录
ls  
# 意义同上，但目录会用“/”标注
ls -F  
# 以行方式列出当前目录下文件的详细信息
ls -l  等价于 ll
#也可以返回目录下某个文件test.txt的详细信息
ls -l test.txt
# 意义同上，但隐藏文件也显示出来
ls -la  
# 按文件大小排序显示
ls -lt  
# 按文件大小排序显示
ls -lS  
# 文件大小转化为易读的方式显示，如KB、MB、GB
ls -lh  
# 递归显示下层目录中的内容
ls -R  
```

4、rm（remove）删除操作

```R
#删除文件file
rm file
#删除目录/文件夹teat
rm -r teat
# 强制删除目录test
rm -rf test
```

5、touch创建文件

```R
#在当前目录下创建名字为test，格式为test的文件
touch test.txt
```

6、cat（concatenate）查看文件内容

```R
#返回test.txt的文件内容
cat test.txt
#分页显示test.txt文件的内容，按空格键向后翻页，按 b 键向前翻页，按 q 键退出
more test.txt
```

## 2、文件操作

1、cp（copy）复制文件

```R
# 文件复制:cp <源文件> <目的位置>
cp 
# 把整个目录/etc/profile复制到当前目录下
cp -r /etc/profile ./d
```

2、mv（move）移动文件

```R
# 移动文件:mv <源文件> <目的位置>
mv MEGA.slurm /Users/gorgeous/Desktop
# 把当前目录下的文件file.txt改名为file1.txt
mv file.txt file1.txt
```

3、ln（link）链接文件----相当于win的快捷方式

```R
# 建立符号链接:ln -s ----相当于win的快捷方式
ln -s <被链接文件名> <链接文件名>
# 建立硬链接----以文件副本的形式存在。但不占用实际空间
ln <被链接文件名> <链接文件名>
```

<img src="/Users/gorgeous/Library/Application Support/typora-user-images/image-20230423182039729.png" alt="image-20230423182039729" style="zoom: 50%;" />



## 3、文件权限

文件权限一般有两种表示方式，分别是用字母表示的权限（**字母权限**）和用数字表示的权限（**数字权限**）

<img src="/Users/gorgeous/Library/Application Support/typora-user-images/image-20230423184548834.png" alt="image-20230423184548834" style="zoom:33%;" />



![image-20230423183432649](/Users/gorgeous/Library/Application Support/typora-user-images/image-20230423183432649.png)

1、返回文件test.txt的详细信息（左边第一项即权限信息）

```
ls -l test.txt
```

2、chmod（change mode）修改文件权限

```R
# 修改文件或目录的权限，-R选项表示连同子目录中的所有文件，也都修改设定的权限
chmod [-R] <权限> <文件>
# 把目录abc及其子目录下的所有文件的权限改成755
chmod -R 755 ./abc
# 对file权限进行如下修改：剥夺主人执行权限、赋予组群中的成员读写权限、剥夺其他人的写权限
chmod u-x,g+rw,o-w file
```

3、chown（change owner）修改文件的主人

```R
# 修改文件的主人
chown [-R] <权限> <文件>
# 修改目录abc下全部文件的主人为zsan
chown -R zsan abc
```

4、chgrp（change group）修改文件的组群

```r
# 修改文件的组群
chgrp [-R] <权限> <文件>
# 修改目录abc的组群为class
chgrp -R class abc
```

##4、文件的压缩/解压

1、tar（*tape archive*）主要用于“打包(将一大堆文件或目录什么的变成一个总的文件)”与“解打包“































