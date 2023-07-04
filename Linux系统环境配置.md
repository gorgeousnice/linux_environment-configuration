# Linux系统环境配置

## 1、安装 miniconda

Step1：在开源的清华镜像网站https://mirrors.tuna.tsinghua.edu.cn寻找下载的版本信息

Tips：镜像网站：把一个互联网上的网站数据“拷贝”到本地服务器，并保持本地服务器数据的同步更新



Step2：选择较新的版本安装，复制名字：

<img src="/Users/gorgeous/Library/Application Support/typora-user-images/image-20230424162624240.png" alt="image-20230424162624240" style="zoom:50%;" />

Step3：在terminal输入代码安装：(这一步相当于win下载安装包)

```R
#wget <option> <url>-软件版本信息
wget --no-check-certificate https://mirrors.bfsu.edu.cn/anaconda/miniconda/Miniconda3-py39_23.1.0-1-Linux-x86_64.sh
```

![image-20230424162245830](/Users/gorgeous/Library/Application Support/typora-user-images/image-20230424162245830.png)



Step4：输入代码运行刚下载好的shell格式文件：（这一步相当于打开win的安装包去安装）

```
bash Miniconda3-py39_23.1.0-1-Linux-x86_64.sh
```

![image-20230424163443748](/Users/gorgeous/Library/Application Support/typora-user-images/image-20230424163443748.png)

Step5：继续，并同意里面的licence；

<img src="/Users/gorgeous/Library/Application Support/typora-user-images/image-20230424172154740.png" alt="image-20230424172154740" style="zoom:70%;" />

enter确认安装位置：

<img src="/Users/gorgeous/Library/Application Support/typora-user-images/image-20230424164306495.png" alt="image-20230424164306495" style="zoom:70%;" />

yes（相当于win的立即运行）

<img src="/Users/gorgeous/Library/Application Support/typora-user-images/image-20230424172415030.png" alt="image-20230424172415030" style="zoom:67%;" />

安装完毕：

![image-20230424165436838](/Users/gorgeous/Library/Application Support/typora-user-images/image-20230424165436838.png)

Step6：执行环境变量，进入conda环境（相当于win的立即运行，和running conda init同理）

```
source ~/.bashrc
```



## 2、配置镜像地址

根据清华镜像网站https://mirrors4.tuna.tsinghua.edu.cn/help/anaconda/使用帮助配置：

Step1：创建`.condarc` 文件来使用 TUNA 镜像源

```
vim .condarc
```



Step2：vim 是 Linux 中最通用的全屏幕文本编辑器,将帮助配置的代码输入到编辑器

```R
channels:
  - defaults
show_channel_urls: true
default_channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch-lts: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
```

Step3：保存并退出vim

<img src="/Users/gorgeous/Library/Application Support/typora-user-images/image-20230424180849222.png" alt="image-20230424180849222" style="zoom:80%;" />

Step4：清除索引缓存，保证用的是镜像站提供的索引

```
conda clean -i
```

![image-20230424180951811](/Users/gorgeous/Library/Application Support/typora-user-images/image-20230424180951811.png)

好像不对，修改vim

![image-20230424181945921](/Users/gorgeous/Library/Application Support/typora-user-images/image-20230424181945921.png)



## 3、安装R

1、创建环境：避免版本以及依赖冲突

```R
conda create --name Renv#
conda activate Renv #激活Renv环境变量
conda deactivate #关闭当前环境(命令后不用接环境变量名称)
```

！！！记得激活在安装，我后面就忘了

2、在镜像中查看R的版本信息：

```
conda search R
```

![image-20230424194228319](/Users/gorgeous/Library/Application Support/typora-user-images/image-20230424194228319.png)我也不知道为什么显示这么少

3、安装R

```
##从conda-forge拉取4.1版本的 `r-base`进行安装
conda install -c conda-forge r-base=4.2
```

![image-20230424194813053](/Users/gorgeous/Library/Application Support/typora-user-images/image-20230424194813053.png)





## 4、R的镜像配置

1、运行R（直接输入字母R即可）

<img src="/Users/gorgeous/Library/Application Support/typora-user-images/image-20230424195107490.png" alt="image-20230424195107490" style="zoom:70%;" />

2、基本操作：

```R
.libPaths()#查看R的library的路径
which R#查看R的路径
q()#退出R
```

3、切换工作目录：

```R
cd miniconda3/lib/R#因为我没有激活Revn,所以路径是在可视化那边找的
```

![image-20230424202329472](/Users/gorgeous/Library/Application Support/typora-user-images/image-20230424202329472.png)

4、以行方式列出R文件的详细信息

<img src="/Users/gorgeous/Library/Application Support/typora-user-images/image-20230424202853298.png" alt="image-20230424202853298" style="zoom:67%;" />

5、输入配置代码到vim新建Rprofile.site文件：文件Rprofile.site为R初期必须执行的文件

```R
cd etc#切换目录
vim Rprofile.site#新建进入编辑器
#按i后输入一下内容：
options("repos" =
c(CRAN="https://mirrors.tuna.tsinghua.edu.cn/CRAN/"))
options(BioC_mirror="https://mirrors.tuna.tsinghua.edu.cn/biocondu
ctor")
#按esc后输入:wq 再enter
```

6、进入R，查看是否配置成功：

```linux
options()$repos
```

![image-20230424203909270](/Users/gorgeous/Library/Application Support/typora-user-images/image-20230424203909270.png)

配置成功



## 5、安装Seurat包

进入r,输入代码：

```
install.packages("Seurat")
```

###关于Seurat：

Seurat是R语言中被用于单细胞RNA-seq质控、分析的一个r包。从而时用户可以鉴定来自单细胞转录本测定的异质性来源。

其中，Seurat包的应用主要包含了：数据导入、数据过滤、数据归一化、特征选择、数据缩放、数据降维、聚类、数据可视化以及差异表达基因分析的功能。









